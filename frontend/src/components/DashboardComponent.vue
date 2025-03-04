<template>
    <div>
      <h2>Dashboard</h2>
      <p>Welcome, {{ userName }}</p>
      <button @click="logout">Logout</button>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        userName: '',
      };
    },
    async created() {
      try {
        const token = localStorage.getItem('token');
        if (!token) {
          this.$router.push('/login');
          return;
        }
        const response = await axios.get('http://localhost:5000/dashboard', {
          headers: { Authorization: token },
        });
        this.userName = response.data.message;
      } catch (err) {
        localStorage.removeItem('token');
        this.$router.push('/login');
      }
    },
    methods: {
      logout() {
        localStorage.removeItem('token');
        this.$router.push('/login');
      },
    },
  };
  </script>
  