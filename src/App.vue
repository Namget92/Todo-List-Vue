<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import taskMaster from "./components/taskMaster.vue";
</script>

<template>
  <img alt="Vite logo" src="./assets/logo2.png" />
  <img alt="Vue logo" src="./assets/logo.png" />
  <h5>Todo List made with Vite & Vue</h5>
  <br />
  <taskMaster />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h5 {
  margin: 0;
}
</style>
