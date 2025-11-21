<script setup>
  import { Button } from './components/ui/button';
  import Login from './pages/Login.vue';
import { useUserStore } from './stores/user';
  import "./style.css"
  import Navbar from './components/navbar.vue';
  import Footer from './components/Footer.vue';
import { onMounted } from 'vue';

  // const isAuth = localStorage.getItem("session_id_utm_ttms")
  const user =  localStorage.getItem("session_id_utm_ttms") ? useUserStore() : null

  onMounted(() => {
    if (user && !user.isLoggedIn) {
      // If there's a session ID in localStorage but the user store is not logged in, set the user as logged in
      user.isLoggedIn = true;
      // Optionally, you can fetch and set other user details here if needed
    }
  });
</script>

<template>
  <Navbar v-if="user.isLoggedIn"/>
  <router-view />
  <Footer/>
</template>

<style scoped></style>
