<script setup>
  import { ref } from 'vue'

  const rules = {
    required: value => !!value || 'Required.',
    min: v => v.length >= 8 || 'Min 8 characters',
    emailMatch: () => (`The email and password you entered don't match`),
  }

  const show1 = ref(false)
  const show2 = ref(true)
  const password = ref(null)

</script>

<template>
    <v-container style="background-color:#E1F5FE" width="50%" class="text-center mt-12">
        <v-row>
            <v-col md="12">
                <v-form>
                    <v-row>
                        <v-col md="12">
                            <div class="text-display-small font-weight-medium">
                                Welcome to MacFit
                            </div>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col md="12">
                            <v-text-field
                                label="Username"
                                type="email"
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
                                type="Password"

                                
                            ></v-text-field>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col md="12">
                            <v-btn color="#1B8FAA"variant="elevated">
                                Login
                            </v-btn>
                        </v-col>
                    </v-row>
                    <v-row>
                            <v-col md="12">
                                <div> New to MacFit Gym? Create an account</div>
                            </v-col>

                        </v-row>

                </v-form>
            </v-col>
        </v-row>
    </v-container>
</template>