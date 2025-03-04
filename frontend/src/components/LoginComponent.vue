<template>
    <div>
      <h2>Login</h2>
      <form @submit.prevent="login">
        <input type="email" v-model="email" placeholder="Email" required />
        <input type="password" v-model="password" placeholder="Password" required />
        <button type="submit">Login</button>
        <p v-if="error">{{ error }}</p>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        email: '',
        password: '',
        error: '',
      };
    },
    methods: {
      async login() {
        try {
          const response = await axios.post('http://localhost:5000/login', {
            email: this.email,
            password: this.password,
          });
          localStorage.setItem('token', response.data.token);
          this.$router.push('/dashboard');
        } catch (err) {
          this.error = err.response.data.message || "Login failed!";
        }
      },
    },
  };
  </script>
  