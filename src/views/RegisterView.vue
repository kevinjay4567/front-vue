<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const name = ref(null);
const email = ref(null);
const password = ref(null);
const router = useRouter();

// register user in the database
function registerUser() {
  fetch('http://127.0.0.1:8000/api/users', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify({
      name: name.value,
      email: email.value,
      password: password.value,
    }),
  })
    .then((res) => res.json())
    .then((json) => console.log(json))
    .catch((err) => console.log(err));

  // clear the form
  document.getElementById('name').value = '';
  document.getElementById('email').value = '';
  document.getElementById('password').value = '';

  router.push('/login');
}
</script>
<template>
  <div class="register-container">
    <h1>Register View</h1>
    <form @submit.prevent="registerUser()" class="register-form">
      <label for="name">Name</label>
      <input type="text" id="name" v-model="name" />
      <label for="email">Email</label>
      <input type="email" id="email" v-model="email" />
      <label for="password">Password</label>
      <input type="password" id="password" v-model="password" />
      <button type="submit">Register</button>
    </form>
  </div>
</template>
<style scoped>
.register-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 90vh;
}

.register-form {
  display: flex;
  padding: 2rem;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  background-color: rgb(61, 61, 118);
  border-radius: 1rem;
  box-shadow: rgb(159, 158, 158) 3px 3px 35px 1px;
}
</style>
