<script setup>
import { RouterLink, RouterView } from 'vue-router';
</script>

<template>
  <nav>
    <RouterLink to="/home">Home</RouterLink>
    <RouterLink to="/register">Register</RouterLink>
    <RouterLink to="/login">Login</RouterLink>
  </nav>
  <RouterView />
</template>

<style scoped>
</style>
