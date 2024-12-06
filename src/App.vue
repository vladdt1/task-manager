<template>
  <div id="app">
    <h1>Список задач</h1>
    <TaskList />
  </div>
</template>

<script setup>
import TaskList from './components/TaskList.vue';
</script>

<style scoped>
#app {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  text-align: center;
  color: #333;
}
</style>
