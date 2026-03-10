<script setup>

</script>

<template>
    <v-container max-width="100%">
        <v-row>
            <v-carousel>
                <v-carousel-item src="/carousel1.jpg" cover></v-carousel-item>    
                <v-carousel-item src="/carousel2.jpg" cover></v-carousel-item>
                <v-carousel-item src="/carousel3.jpg" cover></v-carousel-item>
            </v-carousel>    
        </v-row>        
    </v-container>

   <!--About Us -->
    <v-container color style="background-color:#CFD0D6" max-width="100%">
        <v-row>
            <v-col md="8" class="text-center">
                <div class="text-display-medium mb-12">Welcome to MacFit Gym</div>
                <div class="text-title-large font-weight-light text-medium-emphasis mb-8">At MacFit Gym, we prioritize inclusivity, comfort, and performance. Our Ladies-Only Gym offers a secure, empowering environment with privacy, modern equipment, women-focused classes, personalized training, and professional female coaches dedicated to your success.</div>
                <div class="text-title-large font-weight-light text-medium-emphasis mb-8">Our Men’s Fitness Zone provides a high-performance space for building strength, endurance, and muscle definition, featuring heavy-duty machines, functional rigs, and programs tailored to men’s goals.</div>
                <div class="text-title-large font-weight-light text-medium-emphasis mb-8">Both sections include steam rooms for a rejuvenating finish after every workout. Discover the future of affordable fitness in Kenya with MacFit Gym—where your comfort, confidence, and results come first.</div>
                <v-btn color="#1B8FAA">LEARN MORE</v-btn>
        </v-col>    
        <v-col md="4">
            <v-container class="d-flex align-center-justify-center fill-height"></v-container>
            <v-img src="/public/youcef-chenzer-Zwrrfoh4VSM-unsplash.jpg"></v-img>
        </v-col>
    </v-row>
</v-container>


    <!-- Latest News -->
    <v-container>
        <v-row>
            <v-col md="4">
                <v-card>
                    <v-img src="/dumbbells.jpg" cover></v-img>
                    <v-card-title>Have you lifted the weights?</v-card-title>
                    <v-card-text>Essential for building muscle, strength, and stability through unilateral, full-range-of-motion training that fixes imbalances</v-card-text>
                    <v-btn color="#3A4B68">READ MORE</v-btn>
                </v-card>
            </v-col>
            <v-col md="4">
                <v-card>
                    <v-img src="/kettlebell.jpg" cover></v-img>
                    <v-card-title>Activate your triceps and biceps movements</v-card-title>
                    <v-card-text>Highly effective for simultaneously building functional strength, explosive power, and cardiovascular endurance.</v-card-text>
                    <v-btn color="#3A4B68">READ MORE</v-btn>
                </v-card>
            </v-col>
            <v-col md="4">
                <v-card>
                    <v-img src="/treadmill.jpg" cover></v-img>
                    <v-card-title>Are you so much into cardio?</v-card-title>
                    <v-card-text>This is highly valuable for cardiovascular health, efficient calorie burning, and strengthening muscles and bones.</v-card-text>
                    <v-btn color="#3A4B68">READ MORE</v-btn>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
    
  
    <!--Reviews-->
     <v-container>
        <v-row>
            <v-col md="3">
                <v-card color="#CFD0D6">
                    <v-card-text> MacFit is the best gym in Nairobi</v-card-text>
                    <v-rating :length="5" :size="32" :model-value="5" active-color="primary"></v-rating>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card color="#CFD0D6">
                    <v-card-text> I loved the trainers and the equipment in the gym</v-card-text>
                    <v-rating :length="5" :size="32" :model-value="4" active-color="primary"></v-rating>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card color="#CFD0D6">
                    <v-card-text> This is a good gym with nice trainers and classes</v-card-text>
                    <v-rating :length="5" :size="32" :model-value="3" active-color="primary"></v-rating>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card color="#CFD0D6">
                    <v-card-text> I love MacFit, I can't wait to be back</v-card-text>
                    <v-rating :length="5" :size="32" :model-value="5" active-color="primary"></v-rating>
                </v-card>
            </v-col>
        </v-row>
     </v-container>
    
    <!-- Contact Us -->
    <v-container style="background-color:#CFD0D6" max-width="100%">
        <v-row class="text-center">
        <div class="text-title-large font-weight-light text-medium-emphasis mb-8">Get in Touch.</div>
        <div class="text-title-large font-weight-light text-medium-emphasis mb-8">0797160822 | rahmanhamisi945@gmail.com.</div>
        <div class="text-title-large font-weight-light text-medium-emphasis mb-8">Opening Hours.</div>
        <div class="text-title-large font-weight-light text-medium-emphasis mb-8">Mon-Fri: 5:00am - 2200Hrs.</div>
        <div class="text-title-large font-weight-light text-medium-emphasis mb-8">MacFit Gym, 4th Floor,Craig Mall, Riverside Drive.</div>
        <div class="text-title-large font-weight-light text-medium-emphasis mb-8">&copy; 2025 MacFit. Designed by Rahman Empire</div>
        </v-row>
        </v-container>
</template>    
    