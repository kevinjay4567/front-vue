<script setup>
import { ref } from 'vue';

const data = ref(null);
const error = ref(null);

fetch('http://127.0.0.1:8000/api/users')
  .then((res) => res.json())
  .then((json) => (data.value = json))
  .catch((err) => (error.value = err));
</script>

<template>
  <div v-if="error">Oops! Error encountered: {{ error.message }}</div>
  <div v-else-if="data">
    Data loaded:
    <ul>
      <li v-for="user in data" :key="user.id">
        {{ user.name }}
      </li>
    </ul>
  </div>
  <div v-else>Loading...</div>
</template>
