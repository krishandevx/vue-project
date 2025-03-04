
<template>
  <div id="app">
    <DashboardComponent />
    <LoginComponent />
    <RegisterComponent />
  </div>
</template>

<script>
import DashboardComponent from "./components/DashboardComponent.vue";
import LoginComponent from "./components/LoginComponent.vue";
import RegisterComponent from "./components/RegisterComponent.vue";

export default {
  name: 'App',
  components: {
    DashboardComponent,
    LoginComponent,
    RegisterComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
