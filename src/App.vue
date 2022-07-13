<template>
  <UserGenerator />
</template>

<script setup lang="ts">
import UserGenerator from './components/UserGenerator.vue';
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: center;
}
.container{
  max-width: 500px;
  margin: 0px auto;
}
</style>
