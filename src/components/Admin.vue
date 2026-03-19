<script setup>
import { ref, onMounted } from 'vue'
import api from '../services/api';

const token = localStorage.getItem('authToken');
const error = ref('');
const loading = ref(false);
const tab = ref(1);

// Dialogs
const showAddUserDialog = ref(false)
const showEditUserDialog = ref(false)
const showChangeRoleDialog = ref(false)
const showAddRoleDialog = ref(false)
const showAddEquipmentDialog = ref(false)

// Models
const users = ref([]);
const roles = ref([]);
const equipment = ref([]);

// User form
const firstName = ref('');
const lastName = ref('');
const email = ref('');
const phoneNumber = ref('');
const gender = ref('');
const dob = ref('');
const gymLocation = ref('');
const userRole = ref('');
const userImage = ref(null);
const editingUserId = ref(null);

// Role form
const roleName = ref('');
const abilities = ref('');
const editingRoleId = ref(null);

// Equipment form
const equipmentName = ref('');
const usage = ref('');
const modelNo = ref('');
const equipmentValue = ref('');
const status = ref('');
const editingEquipmentId = ref(null);

// Validation rules
const rules = {
  required: value => !!value || 'Required.',
}

// ---------------- FETCH DATA ----------------
async function fetchUsers() {
  try {
    const res = await api.get('users', { headers: { Authorization: `Bearer ${token}` } });
    users.value = res.data;
  } catch (err) {
    error.value = err.response?.data?.message || 'Failed to fetch users';
  }
}

async function fetchRoles() {
  try {
    const res = await api.get('roles', { headers: { Authorization: `Bearer ${token}` } });
    roles.value = res.data;
  } catch (err) {
    error.value = 'Failed to fetch roles';
  }
}

async function fetchEquipment() {
  try {
    const res = await api.get('getEquipments', { headers: { Authorization: `Bearer ${token}` } });
    equipment.value = res.data;
  } catch (err) {
    error.value = err.response?.data?.message || 'Failed to fetch equipment';
  }
}

// ---------------- ADD / EDIT USER ----------------
async function addUser() {
  loading.value = true;
  const formData = new FormData();
  formData.append("name", firstName.value + ' ' + lastName.value);
  formData.append("email", email.value);
  formData.append("phoneNumber", phoneNumber.value);
  formData.append("dob", dob.value);
  formData.append("gender", gender.value);
  formData.append("gymLocation", gymLocation.value);
  formData.append("role_id", userRole.value);
  if (userImage.value) formData.append("user_image", userImage.value);

  try {
    await api.post('users', formData, { headers: { Authorization: `Bearer ${token}` } });
    loading.value = false;
    closeUserDialog();
    fetchUsers();
  } catch (err) {
    error.value = err.response?.data?.messages || 'Failed to add user';
    loading.value = false;
  }
}

function editUser(user) {
  editingUserId.value = user.id;
  const nameParts = user.name.split(' ');
  firstName.value = nameParts[0];
  lastName.value = nameParts.slice(1).join(' ');
  email.value = user.email;
  phoneNumber.value = user.phoneNumber;
  dob.value = user.dob;
  gender.value = user.gender;
  gymLocation.value = user.gymLocation;
  userRole.value = user.role_id;
  userImage.value = null;
  showEditUserDialog.value = true;
}

async function updateUser() {
  loading.value = true;
  const formData = new FormData();
  formData.append("name", firstName.value + ' ' + lastName.value);
  formData.append("email", email.value);
  formData.append("phoneNumber", phoneNumber.value);
  formData.append("dob", dob.value);
  formData.append("gender", gender.value);
  formData.append("gymLocation", gymLocation.value);
  formData.append("role_id", userRole.value);
  if (userImage.value) formData.append("user_image", userImage.value);

  try {
    await api.post(`users/${editingUserId.value}`, formData, { headers: { Authorization: `Bearer ${token}` } });
    loading.value = false;
    closeUserDialog();
    fetchUsers();
  } catch (err) {
    error.value = err.response?.data?.messages || 'Failed to update user';
    loading.value = false;
  }
}

// ---------------- CHANGE ROLE ----------------
function changeRole(user) {
  editingUserId.value = user.id;
  userRole.value = user.role_id;
  showChangeRoleDialog.value = true;
}

async function updateRole() {
  try {
    await api.post(`users/${editingUserId.value}/role`, { role_id: userRole.value }, { headers: { Authorization: `Bearer ${token}` } });
    showChangeRoleDialog.value = false;
    fetchUsers();
  } catch (err) {
    error.value = 'Failed to update role';
  }
}

// ---------------- ADD ROLE ----------------
async function addRole() {
  loading.value = true;
  const payload = { name: roleName.value, abilities: abilities.value ? abilities.value.split(',') : [] };
  try {
    await api.post('roles', payload, { headers: { Authorization: `Bearer ${token}` } });
    loading.value = false;
    closeRoleDialog();
    fetchRoles();
  } catch (err) {
    error.value = err.response?.data?.messages || 'Failed to add role';
    loading.value = false;
  }
}

// ---------------- ADD EQUIPMENT ----------------
async function addEquipment() {
  const formData = new FormData();
  formData.append("name", equipmentName.value);
  formData.append("usage", usage.value);
  formData.append("model_no", modelNo.value);
  formData.append("value", equipmentValue.value);
  formData.append("status", status.value);

  try {
    await api.post('saveEquipment', formData, { headers: { Authorization: `Bearer ${token}` } });
    closeEquipmentDialog();
    fetchEquipment();
  } catch (err) {
    error.value = err.response?.data?.messages || 'Failed to add equipment';
  }
}

// ---------------- CLOSE DIALOGS ----------------
function closeUserDialog() {
  showAddUserDialog.value = false;
  showEditUserDialog.value = false;
  editingUserId.value = null;
  firstName.value = lastName.value = email.value = phoneNumber.value = gender.value = dob.value = gymLocation.value = userRole.value = '';
  userImage.value = null;
}

function closeRoleDialog() {
  showAddRoleDialog.value = false;
  roleName.value = '';
  abilities.value = '';
}

function closeEquipmentDialog() {
  showAddEquipmentDialog.value = false;
  equipmentName.value = usage.value = modelNo.value = equipmentValue.value = status.value = '';
}

// ---------------- ON MOUNT ----------------
onMounted(() => {
  fetchUsers();
  fetchRoles();
  fetchEquipment();
});
</script>
<template>
  <v-container class="text-center mt-12" style="background-color:#CFD0D6">
    <v-card>
      <v-tabs v-model="tab" align-tabs="center" color="primary">
        <v-tab :value="1">Users</v-tab>
        <v-tab :value="2">Roles</v-tab>
        <v-tab :value="3">Equipment</v-tab>
      </v-tabs>

      <v-tabs-window v-model="tab">
        <!-- USERS TAB -->
        <v-tabs-window-item :value="1">
          <v-container>
            <v-row align="right">
              <v-col cols="12">
                <v-btn color="blue-darken-2" icon="mdi-plus" @click="showAddUserDialog = true"></v-btn>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <v-table class="border">
                  <thead>
                    <tr>
                      <th>Image</th><th>Name</th><th>Email</th><th>Phone</th><th>DOB</th><th>Gender</th><th>Role</th><th>Gym</th><th>Actions</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="user in users" :key="user.id">
                      <td><v-avatar size="40"><img :src="user.user_image ? '/storage/'+user.user_image : 'https://via.placeholder.com/40'" /></v-avatar></td>
                      <td>{{ user.name }}</td>
                      <td>{{ user.email }}</td>
                      <td>{{ user.phoneNumber }}</td>
                      <td>{{ user.dob }}</td>
                      <td>{{ user.gender }}</td>
                      <td>{{ user.role?.name }}</td>
                      <td>{{ user.gymLocation }}</td>
                      <td>
                        <v-btn color="success" small @click="changeRole(user)">Change Role</v-btn>
                        <v-btn color="primary" small @click="editUser(user)">Edit</v-btn>
                      </td>
                    </tr>
                  </tbody>
                </v-table>
              </v-col>
            </v-row>
          </v-container>
        </v-tabs-window-item>

        <!-- ROLES TAB -->
        <v-tabs-window-item :value="2">
          <v-container>
            <v-row align="right"><v-col cols="12"><v-btn color="blue-darken-2" icon="mdi-plus" @click="showAddRoleDialog = true"></v-btn></v-col></v-row>
            <v-row><v-col>
              <v-table class="border">
                <thead><tr><th>Name</th><th>Abilities</th><th>No of Users</th></tr></thead>
                <tbody>
                  <tr v-for="role in roles" :key="role.id">
                    <td>{{ role.name }}</td>
                    <td>{{ role.abilities }}</td>
                    <td>{{ role.users_count }}</td>
                  </tr>
                </tbody>
              </v-table>
            </v-col></v-row>
          </v-container>
        </v-tabs-window-item>

        <!-- EQUIPMENT TAB -->
        <v-tabs-window-item :value="3">
          <v-container>
            <v-row align="right"><v-col cols="12"><v-btn color="blue-darken-2" icon="mdi-plus" @click="showAddEquipmentDialog = true"></v-btn></v-col></v-row>
            <v-row><v-col>
              <v-table class="border">
                <thead><tr><th>Name</th><th>Model</th><th>Value</th><th>Usage</th><th>Status</th></tr></thead>
                <tbody>
                  <tr v-for="eq in equipment" :key="eq.id">
                    <td>{{ eq.name }}</td>
                    <td>{{ eq.model_no }}</td>
                    <td>{{ eq.value }}</td>
                    <td>{{ eq.usage }}</td>
                    <td>{{ eq.status }}</td>
                  </tr>
                </tbody>
              </v-table>
            </v-col></v-row>
          </v-container>
        </v-tabs-window-item>
      </v-tabs-window>
    </v-card>
  </v-container>
</template>