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

  const confirmPassword = ref(null)
  const show1confirmP= ref(false)

</script>

<template>
    <v-container style="background-color:#E1F5FE" width="50%" class="text-center mt-12">
        <v-row>
            <v-col md="12">
                <v-form>
                    <v-row>
                        <v-col md="12">
                            <div class="text-display-small font-weight-medium">
                                Join MacFit Gym
                            </div>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col md="12">
                            <v-text-field
                                label="Firstname"
                                
                                variant="outlined"
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="12">
                            <v-text-field
                                label="Lastname"
                                
                                variant="outlined"
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="12">
                            <v-text-field
                                label="email"
                                
                                variant="outlined"
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="12">
                            <v-text-field
                                label="Phone Number"
                                
                                variant="outlined"
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="12">
                            <v-radio-group inline="">
                                <v-radio label="Male" value="one"></v-radio>
                                <v-radio label="Female" value="two"></v-radio>
                                </v-radio-group>
                                <v-text-field
                                
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="12">
                            <v-date-input variant="outlined"></v-date-input>
                        </v-col>
                    </v-row>    
                    <v-row>
                        <v-col md="12">
                            <v-select>
                                
                                label="Select"
                                :items="['Nairobi', 'Westlands', 'Lavington', 'Riverside Drive', 'Texas', 'Wyoming']"
                                variant="outlined"
                                </v-select>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col md="12">
                            <div class="text-title-large font-weight-medium text-right"></div>
                            <v-text-field
                                v-model="confirmPassword"
                                :append-icon="show1Confirm ? 'mdi-eye' : 'mdi-eye-off'"
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