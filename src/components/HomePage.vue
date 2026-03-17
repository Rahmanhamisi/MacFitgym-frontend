
<script setup>

</script>

<template>

<v-container fluid class="pa-0">

  <!-- HERO SECTION WITH BACKGROUND IMAGE -->
  <v-img
    src="/public/strong-man-training-gym.jpg"
    height="500"
    cover
  >

    <v-row
      class="fill-height"
      align="center"
      justify="center"
      style="background: rgba(0,0,0,0.5);"
    >

      <v-col cols="12" class="text-center text-white">

        <v-icon size="70">mdi-dumbbell</v-icon>

        <div class="text-h3 font-weight-bold mt-4">
          Welcome to MacFit Gym
        </div>

        <div class="text-subtitle-1 mt-2">
          Train smart • Stay strong • Live Healthy
        </div>

        <v-btn
          class="mt-6"
          size="large"
          color="#1B8FAA"
          to="/bundles"
        >
          View Membership Bundles
        </v-btn>

      </v-col>

    </v-row>

  </v-img>


  <!-- FEATURES -->
  <v-container class="mt-16">

    <v-row class="text-center">

      <v-col md="4">
        <v-icon size="60" color="#1B8FAA">
          mdi-dumbbell
        </v-icon>

        <div class="text-h6 font-weight-bold mt-3">
          Modern Equipment
        </div>

        <div>
          Train with genuine professional gym machines.
        </div>
      </v-col>


      <v-col md="4">
        <v-icon size="60" color="#1B8FAA">
          mdi-account-group
        </v-icon>

        <div class="text-h6 font-weight-bold mt-3">
          Professional Trainers
        </div>

        <div>
          Expert trainers to guide your fitness journey.
        </div>
      </v-col>


     <v-col md="4">
        <v-icon size="60" color="#1B8FAA">
        mdi-run
        </v-icon>

        <div class="text-h6 font-weight-bold mt-3">
        Workout Programs
  </div>

  <div>
    Strength training, cardio workouts, and customized fitness programs.
  </div>
</v-col>

    </v-row>

  </v-container>

</v-container>

</template>

