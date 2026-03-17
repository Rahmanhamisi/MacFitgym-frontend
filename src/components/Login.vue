<script setup>
  import { ref } from 'vue'
  import { useRouter } from "vue-router"
  import { useAuth } from '../services/auth'

    const router = useRouter()
    const { login, loading, error } = useAuth()

  const rules = {
    required: value => !!value || 'Required.',
    min: v => v.length >= 8 || 'Min 8 characters',
    emailMatch: () => (`The email and password you entered don't match`),
  }

  const show1 = ref(false)
  const show2 = ref(true)
  const password = ref(null)

  const username = ref(null)

 async function handleLogin(){
  
  if (!username.value || !password.value) {
    console.error('Email and password are required')
    return
  }
  
  try {
    await login({
      email: username.value,
      password: password.value
    })
   
    // Redirect after successful login
    router.push('/homepage').then(() => {
        router.go(0); // Reloads the current route
    });
  } catch (err) {
    // Error is already handled by the auth service
    console.error('Login failed', err)
  }
}

</script>

<template>
    <v-container style="background-color:#E1F5FE" width="50%" class="text-center mt-12">
        <v-row>
            <v-col md="12">
                <v-form>
                    <v-row>
                        <v-col md="12">
                            <div class="text-display-small font-weight-medium">
                                Welcome to MacFit Gym
                            </div>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col md="12">
                            <v-text-field
                                label="Username"
                                v-model="username"
                                variant="outlined"
                            ></v-text-field>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col md="12">
                            <v-text-field
                                v-model="password"
                                :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                                :rules="[rules.required, rules.min]"
                                :type="show1 ? 'text' : 'password'"
                                variant="outlined"
                                @click:append="show1 = !show1"
                                label="Password"

                                
                            ></v-text-field>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col md="12">
                            <v-btn color="#1B8FAA"variant="elevated"@click="handleLogin">Log in</v-btn>  
                        </v-col>
                    </v-row>
                    <v-row>
                            <v-col md="12">
                                <div> New to MacFit Gym? 
                                <router-link to="/signup">Create an account</router-link></div>
                            </v-col>

                        </v-row>

                </v-form>
            </v-col>
        </v-row>
    </v-container>
</template>