<script setup>

</script>

<template>
    <v-container style="background-color:#CFD0D6" class="mt-12">
        <v-row>
            <div class="text-display-medium mb-12">Bundles and Pricing</div>
        </v-row>
        <v-row>
            <v-col md="3">
                <v-card class="text-center">
                    <v-icon color="#3A4B68" icon="mdi-clock-outline" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#3A4B68">Daily Pass</v-card-title>
                    <v-card-text>500 Ksh</v-card-text>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card class="text-center">
                    <v-icon color="#3A4B68" icon="mdi-calendar-blank" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#3A4B68">1 Month</v-card-title>
                    <v-card-text>5500 Ksh</v-card-text>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card class="text-center">
                    <v-icon color="#3A4B68" icon="mdi-numeric-3-circle-outline" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#3A4B68">3 Months</v-card-title>
                    <v-card-text>15000 Ksh</v-card-text>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card class="text-center">
                    <v-icon color="#3A4B68" icon="mdi-numeric-6-circle-outline" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#3A4B68">6 Months</v-card-title>
                    <v-card-text>25000 Ksh</v-card-text>
                </v-card>
            </v-col>
        </v-row>
        <v-row>
            <v-col md="12">
                <v-card class="text-center">
                    <v-icon color="#3A4B68" icon="mdi-timer-sand-full" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#3A4B68">12 Months</v-card-title>
                    <v-card-text>45000 Ksh</v-card-text>
                </v-card>
            </v-col>
        </v-row>

    </v-container>

    <!-- what is included -->
     <v-container>
        <v-row>
            <v-col md="12">
                <div class="text-display-medium mb-12">What's included in your bundle</div>
            </v-col>
        </v-row>
        <v-row>
            <v-col md="3">
                <v-card>
                    <v-icon color="#00695C" icon="mdi-timer-sand-full" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#3A4B68">Samba</v-card-title>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card>
                    <v-icon color="#00695C" icon="mdi-timer-sand-full" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#FF5722">Boxing and Spin</v-card-title>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card>
                    <v-icon color="#00695C" icon="mdi-timer-sand-full" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#FF6F00">Yoga and Lower body circuit</v-card-title>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card>
                    <v-icon color="#00695C" icon="mdi-timer-sand-full" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#FF6F00">Stick mobility</v-card-title>
                </v-card>
            </v-col>
        </v-row>
        <v-row>
            <v-col md="3">
                <v-card>
                    <v-icon color="#00695C" icon="mdi-timer-sand-full" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#FF6F00">Cardio and core challenge</v-card-title>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card>
                    <v-icon color="#00695C" icon="mdi-timer-sand-full" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#FF6F00">Weight lifting</v-card-title>
                </v-card>
            </v-col>
        </v-row>
     </v-container>
     <!-- How to join -->
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
</template>