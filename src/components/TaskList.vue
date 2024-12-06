<template>
    <div>
      <AddTask @add="addTask" />
      <div v-if="tasks.length === 0">Нет задач!</div>
      <div v-for="task in tasks" :key="task.id">
        <TaskItem :task="task" @remove="removeTask" />
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  import TaskItem from './TaskItem.vue';
  import AddTask from './AddTask.vue';
  
  const tasks = ref([]);
  
  const loadTasks = () => {
    const savedTasks = JSON.parse(localStorage.getItem('tasks')) || [];
    tasks.value = savedTasks;
  };
  
  const saveTasks = () => {
    localStorage.setItem('tasks', JSON.stringify(tasks.value));
  };
  
  const addTask = (taskText) => {
    const newTask = { id: Date.now(), text: taskText, completed: false };
    tasks.value.push(newTask);
    saveTasks();
  };
  
  const removeTask = (taskId) => {
    tasks.value = tasks.value.filter(task => task.id !== taskId);
    saveTasks();
  };
  
  onMounted(() => {
    loadTasks();
  });
  </script>
  
  <style scoped>
  div {
    padding: 20px;
  }
  
  button {
    margin-left: 10px;
  }
  </style>
  