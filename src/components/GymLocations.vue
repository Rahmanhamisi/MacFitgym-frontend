<script setup>
import "leaflet/dist/leaflet.css"
import * as L from 'leaflet'
import { ref, onMounted } from 'vue'

const cbdMap = ref(null)
const westlandsMap = ref(null)
const lavingtonMap = ref(null)
const kitisuruMap = ref(null)

onMounted(() => {

   cbdMap.value = L.map('cbd-map').setView([-1.2953145569779758, 36.817184449599566], 13)
   L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
       maxZoom: 19,
   }).addTo(cbdMap.value)
   L.marker([-1.3073328374609299, 36.81211146039793]).addTo(cbdMap.value)

   westlandsMap.value = L.map('westlands-map').setView([-1.263, 36.81], 13)
   L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
       maxZoom: 19,
   }).addTo(westlandsMap.value)
   L.marker([-1.263, 36.81]).addTo(westlandsMap.value)

   lavingtonMap.value = L.map('lavington-map').setView([-1.283, 36.776], 13)
   L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
       maxZoom: 19,
   }).addTo(lavingtonMap.value)
   L.marker([-1.283, 36.776]).addTo(lavingtonMap.value)

   kitisuruMap.value = L.map('kitisuru-map').setView([-1.234, 36.78], 13)
   L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
       maxZoom: 19,
   }).addTo(kitisuruMap.value)
   L.marker([-1.234, 36.78]).addTo(kitisuruMap.value)

})
</script>

<template>
<v-container class="mt-12">

   <v-row>
      <v-col>
         <div class="text-display-medium mb-6">Our Locations</div>
      </v-col>
   </v-row>

   <v-row>
      <v-col>
         <v-card>

            <v-row>
               <v-col md="4">
                  <v-card-text>Nairobi CBD</v-card-text>
               </v-col>
               <v-col md="8">
                  <div id="cbd-map" style="height:30vh;"></div>
               </v-col>
            </v-row>

            <v-row>
               <v-col md="4">
                  <v-card-text>Westlands</v-card-text>
               </v-col>
               <v-col md="8">
                  <div id="westlands-map" style="height:30vh;"></div>
               </v-col>
            </v-row>

            <v-row>
               <v-col md="4">
                  <v-card-text>Lavington</v-card-text>
               </v-col>
               <v-col md="8">
                  <div id="lavington-map" style="height:30vh;"></div>
               </v-col>
            </v-row>

            <v-row>
               <v-col md="4">
                  <v-card-text>Kitisuru</v-card-text>
               </v-col>
               <v-col md="8">
                  <div id="kitisuru-map" style="height:30vh;"></div>
               </v-col>
            </v-row>

         </v-card>
      </v-col>
   </v-row>

</v-container>
</template>