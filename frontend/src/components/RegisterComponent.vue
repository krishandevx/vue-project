<template>
    <div>
      <h2>Register</h2>
      <form @submit.prevent="register">
        <input type="text" v-model="fullName" placeholder="Full Name" required />
        <input type="email" v-model="email" placeholder="Email" required />
        <input type="password" v-model="password" placeholder="Password" required />
        <input type="password" v-model="confirmPassword" placeholder="Confirm Password" required />
        <button type="submit">Register</button>
        <p v-if="error">{{ error }}</p>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        fullName: '',
        email: '',
        password: '',
        confirmPassword: '',
        error: '',
      };
    },
    methods: {
      async register() {
        if (this.password !== this.confirmPassword) {
          this.error = "Passwords do not match!";
          return;
        }
        try {
          await axios.post('http://localhost:5000/register', {
            fullName: this.fullName,
            email: this.email,
            password: this.password,
          });
          this.$router.push('/login');
        } catch (err) {
          this.error = err.response.data.error || "Registration failed!";
        }
      },
    },
  };
  </script>
  