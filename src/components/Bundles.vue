```vue
<script setup>
import { ref } from 'vue'
import { useRouter } from "vue-router"

const router = useRouter()

const selectedBundle = ref(null)
const selectedPrice = ref(null)
const showBundleDialog = ref(false)

const isLoggedIn = localStorage.getItem("authToken") === "true"

function showBundle(name, price){
    if(isLoggedIn){
        selectedBundle.value = name
        selectedPrice.value = price
        showBundleDialog.value = true//open popup
        
    }else{
        router.push('/login')
    }
}
function subscribe(){
    const userDetails = JSON.parse(localStorage.getItem('user'))
    userDetails.subscription = {
        name: selectedBundle.value,
        price: selectedPrice.value
    }
    localStorage.setItem('user', JSON.stringify(userDetails))

    

}
</script>

<template>

<v-container style="background-color:#546E7A" class="mt-12">
    
    <v-row>
        <div class="text-display-medium mb-12">Bundles and Pricing</div>
    </v-row>

    <v-row>
    <v-col cols="12">
        <div class="text-label-medium font-italic">
            Click on a bundle to subscribe
        </div>
    </v-col>

        <v-col md="3">
            <v-card class="text-center" @click="showBundle('Daily Pass',500)">
                <v-icon color="#BF360C" icon="mdi-clock-outline" size="large" class="mt-8"></v-icon>
                <v-card-title color="#3A4B68">Daily Pass</v-card-title>
                <v-card-text>500 Ksh</v-card-text>
            </v-card>
        </v-col>

        <v-col md="3">
            <v-card class="text-center" @click="showBundle('1 Month',5500)">
                <v-icon color="#BF360C" icon="mdi-calendar-blank" size="large" class="mt-8"></v-icon>
                <v-card-title color="#3A4B68">1 Month</v-card-title>
                <v-card-text>5500 Ksh</v-card-text>
            </v-card>
        </v-col>

        <v-col md="3">
            <v-card class="text-center" @click="showBundle('3 Months',15000)">
                <v-icon color="#BF360C" icon="mdi-calendar-badge-outline" size="large" class="mt-8"></v-icon>
                <v-card-title color="#3A4B68">3 Months</v-card-title>
                <v-card-text>15000 Ksh</v-card-text>
            </v-card>
        </v-col>

        <v-col md="3">
            <v-card class="text-center" @click="showBundle('6 Months',25000)">
                <v-icon color="#BF360C" icon="mdi-calendar-edit-outline" size="large" class="mt-8"></v-icon>
                <v-card-title color="#3A4B68">6 Months</v-card-title>
                <v-card-text>25000 Ksh</v-card-text>
            </v-card>
        </v-col>

    </v-row>

    <v-row>
        <v-col md="12">
            <v-card class="text-center" @click="showBundle('12 Months',45000)">
                <v-icon color="#BF360C" icon="mdi-calendar-export" size="large" class="mt-8"></v-icon>
                <v-card-title color="#3A4B68">12 Months</v-card-title>
                <v-card-text>45000 Ksh</v-card-text>
            </v-card>
        </v-col>
    </v-row>

</v-container>


<!-- WHAT IS INCLUDED -->

<v-container>

<v-row>
<v-col md="12">
<div class="text-display-medium mb-12">
What is included in your bundle
</div>
</v-col>
</v-row>

<v-row>

<v-col md="3">
<v-card class="text-center pa-4">
<v-icon color="#BF360C" icon="mdi-dumbbell" size="large" class="mt-8"></v-icon>
<v-card-title color="#3A4B68">Arm Check</v-card-title>
</v-card>
</v-col>

<v-col md="3">
<v-card class="text-center pa-4">
<v-icon color="#BF360C" icon="mdi-boxing-glove" size="large" class="mt-8"></v-icon>
<v-card-title color="#2C3E50">Boxing and Spin</v-card-title>
</v-card>
</v-col>

<v-col md="3">
<v-card class="text-center pa-4">
<v-icon color="#BF360C" icon="mdi-weight-lifter" size="large" class="mt-8"></v-icon>
<v-card-title color="#2C3E50">
Weight lifting and upper body circuit
</v-card-title>
</v-card>
</v-col>

<v-col md="3">
<v-card class="text-center pa-4">
<v-icon color="#BF360C" icon="mdi-yoga" size="large" class="mt-8"></v-icon>
<v-card-title color="#2C3E50">Stick mobility</v-card-title>
</v-card>
</v-col>

</v-row>

<v-row>

<v-col md="3">
<v-card class="text-center pa-4">
<v-icon color="#BF360C" icon="mdi-run" size="large" class="mt-8"></v-icon>
<v-card-title color="#2C3E50">Cardio and core challenge</v-card-title>
</v-card>
</v-col>

<v-col md="3">
<v-card class="text-center pa-4">
<v-icon color="#BF360C" icon="mdi-walk" size="large" class="mt-8"></v-icon>
<v-card-title color="#2C3E50">Treadmill walk</v-card-title>
</v-card>
</v-col>

</v-row>

</v-container>


<!-- HOW TO JOIN -->

<v-container>

<v-row>
<v-col>
<div class="text-display-medium mb-12">
How to join
</div>
</v-col>
</v-row>

<v-row>
<v-col>

<v-list>
<v-list-item>1. Select your preferred bundles</v-list-item>
<v-list-item>2. Fill in the online form</v-list-item>
<v-list-item>3. Make a payment</v-list-item>
<v-list-item>4. Visit the gym to activate your bundles</v-list-item>
</v-list>

</v-col>
</v-row>

</v-container>
<!--Dialog -->
<v-dialog v-model="showBundleDialog" width="500">
  <v-card>

    <v-card-title class="text-h5">
      Confirm Subscription
    </v-card-title>

    <v-card-text>
      You selected:

      <div class="mt-3">
        <strong>Bundle:</strong> {{ selectedBundle }}
      </div>

      <div>
        <strong>Price:</strong> {{ selectedPrice }} Ksh
      </div>
    </v-card-text>

    <v-card-actions>

      <v-spacer></v-spacer>

      <v-btn
        color="grey"
        variant="text"
        @click="showBundleDialog = false"
      >
        Cancel
      </v-btn>

      <v-btn
        color="#BF360C"
        variant="elevated"
        @click="subscribe">
        
      
        Proceed
      </v-btn>

    </v-card-actions>

  </v-card>
</v-dialog>

</template>
```
