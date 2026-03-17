<script setup>
import { ref } from 'vue'
import { useRouter } from "vue-router"
import { useAuth } from '../services/auth'

const router = useRouter()
const { register, loading, error } = useAuth()

// validation rules
const rules = {
  required: value => !!value || 'Required.',
  min: v => v?.length >= 8 || 'Min 8 characters',
  passwordMatch: () =>
    password.value === confirmPassword.value || 'Passwords must match'
}

// password visibility
const show1 = ref(false)
const show1confirm = ref(false)

// password models
const password = ref('')
const confirmPassword = ref('')

// form models
const firstName = ref('')
const lastName = ref('')
const email = ref('')
const phoneNumber = ref('')
const gender = ref('')
const dob = ref('')
const gymLocation = ref('')

// signup function
const signUp = async () => {

  const formData = new FormData()
  formData.append("name", firstName.value + " " + lastName.value)
  formData.append("email", email.value)
  formData.append("phoneNumber", phoneNumber.value)
  formData.append("dob", dob.value)
  formData.append("gender", gender.value)
  formData.append("gymLocation", gymLocation.value)
  formData.append("password", password.value)
  formData.append("password_confirmation", confirmPassword.value)
  formData.append("role_id", 4)

  try {

    await register(formData)

    const userDetails = {
      name: firstName.value + " " + lastName.value,
      email: email.value,
      phone: phoneNumber.value,
      dob: dob.value,
      gender: gender.value,
      gymLocation: gymLocation.value
    }

    localStorage.setItem('userDetails', JSON.stringify(userDetails))

    router.push('/').then(() => {
      router.go(0)
    })

  } catch (err) {
    console.error('Sign up failed', err)
  }
}
</script>

<template>
<v-container style="background-color:#E0F7FA" width="50%" class="text-center mt-12">

<v-row>
<v-col md="12">

<v-form>

<v-row>
<v-col md="12">
<v-img src="/barbell.jpg"></v-img>
</v-col>
</v-row>

<v-row>
<v-col>
<div class="text-display-small font-weight-medium">
Sign up for MacFit Gym
</div>
</v-col>
</v-row>

<!-- First Name -->
<v-row>
<v-col md="6">
<div class="text-title-large font-weight-medium text-right">Firstname</div>
</v-col>
<v-col md="6">
<v-text-field v-model="firstName" variant="outlined"></v-text-field>
</v-col>
</v-row>

<!-- Last Name -->
<v-row>
<v-col md="6">
<div class="text-title-large font-weight-medium text-right">Lastname</div>
</v-col>
<v-col md="6">
<v-text-field v-model="lastName" variant="outlined"></v-text-field>
</v-col>
</v-row>

<!-- Email -->
<v-row>
<v-col md="6">
<div class="text-title-large font-weight-medium text-right">Email</div>
</v-col>
<v-col md="6">
<v-text-field v-model="email" type="email" variant="outlined"></v-text-field>
</v-col>
</v-row>

<!-- Phone -->
<v-row>
<v-col md="6">
<div class="text-title-large font-weight-medium text-right">Phone Number</div>
</v-col>
<v-col md="6">
<v-text-field v-model="phoneNumber" type="number" variant="outlined"></v-text-field>
</v-col>
</v-row>

<!-- Gender -->
<v-row>
<v-col md="6">
<div class="text-title-large font-weight-medium text-right">Gender</div>
</v-col>
<v-col md="6">
<v-radio-group inline v-model="gender">
<v-radio label="Male" value="Male"></v-radio>
<v-radio label="Female" value="Female"></v-radio>
</v-radio-group>
</v-col>
</v-row>

<!-- DOB -->
<v-row>
<v-col md="6">
<div class="text-title-large font-weight-medium text-right">Date of Birth</div>
</v-col>
<v-col md="6">
<v-date-input v-model="dob" variant="outlined"></v-date-input>
</v-col>
</v-row>

<!-- Gym Location -->
<v-row>
<v-col md="6">
<div class="text-title-large font-weight-medium text-right">Gym location</div>
</v-col>
<v-col md="6">
<v-select
v-model="gymLocation"
:items="['Nairobi','Westlands','Lavington','Kitisuru']"
label="Select"
variant="outlined"
></v-select>
</v-col>
</v-row>

<!-- Password -->
<v-row>
<v-col md="6">
<div class="text-title-large font-weight-medium text-right">Password</div>
</v-col>
<v-col md="6">
<v-text-field
v-model="password"
:append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
:type="show1 ? 'text' : 'password'"
:rules="[rules.required, rules.min]"
variant="outlined"
@click:append="show1=!show1"
></v-text-field>
</v-col>
</v-row>

<!-- Confirm Password -->
<v-row>
<v-col md="6">
<div class="text-title-large font-weight-medium text-right">Confirm Password</div>
</v-col>
<v-col md="6">
<v-text-field
v-model="confirmPassword"
:append-icon="show1confirm ? 'mdi-eye' : 'mdi-eye-off'"
:type="show1confirm ? 'text' : 'password'"
:rules="[rules.required, rules.passwordMatch]"
variant="outlined"
@click:append="show1confirm=!show1confirm"
></v-text-field>
</v-col>
</v-row>

<v-row>
<v-col md="12">
<v-btn color="#342C2A" @click="signUp">Sign Up</v-btn>
</v-col>
</v-row>

<v-row>
<v-col md="12">
<div>
Already have an account?
<router-link to="/login">Back to login</router-link>
</div>
</v-col>
</v-row>

</v-form>

</v-col>
</v-row>

</v-container>
</template>