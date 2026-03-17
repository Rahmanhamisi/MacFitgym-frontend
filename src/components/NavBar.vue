<script setup>
import { useRouter } from "vue-router";
import { useAuth } from "../services/auth";   // <-- missing import

const { logout } = useAuth()
const router = useRouter();

const isLoggedIn = localStorage.getItem("authToken")
const isAdmin = true

function handleLogout(){
    localStorage.removeItem("isLoggedIn")
    logout();
    router.push('/')
}
</script>

<template>
    <v-app-bar color="#1B8FAA">
        <v-app-bar-title>
            <router-link to="/">MacFit Gym</router-link>
        </v-app-bar-title>

        <v-btn to="/landingpage"></v-btn>

        <v-btn to="/homepage" v-if="isLoggedIn">Home</v-btn>

        <v-btn to="/bundles">Bundles</v-btn>

        <v-btn to="/gym_locations">Our Gyms</v-btn>

        <v-btn to="/admin" v-if="isAdmin">Admin</v-btn>

        <v-btn icon="mdi-account" v-if="isLoggedIn">
            P
            <v-menu activator="parent">
                <v-list>
                    <v-list-item>
                        <v-btn color="primary" to="/profile">Profile</v-btn>
                    </v-list-item>

                    <v-list-item>
                        <v-btn color="primary" @click="handleLogout">Logout</v-btn>
                    </v-list-item>
                </v-list>
            </v-menu>
        </v-btn>

        <v-btn to="/login" v-else>Login</v-btn>
    </v-app-bar>
</template>