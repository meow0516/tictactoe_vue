<script setup lang="ts">
import TicTacToe from './components/TicTacToe.vue';
import '/node_modules/primeflex/primeflex.min.css';
import '/node_modules/primeflex/themes/arya-blue.css';
</script>

<template>
  <TicTacToe />
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
* {
  box-sizing: border-box;
}
</style>
