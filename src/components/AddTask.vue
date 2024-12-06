<template>
    <form @submit.prevent="addTask">
      <input v-model="newTask" type="text" placeholder="Новая задача" required />
      <button type="submit">Добавить</button>
    </form>
  </template>
  
  <script setup>
  import { ref, defineEmits } from 'vue';
  
  const emit = defineEmits();
  const newTask = ref('');
  
  const addTask = () => {
    if (newTask.value.trim()) {
      emit('add', newTask.value.trim());
      newTask.value = ''; // Очистить поле ввода после добавления
    }
  };
  </script>
  
  <style scoped>
  form {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
  }
  
  input {
    flex-grow: 1;
    padding: 10px;
  }
  
  button {
    padding: 10px;
    background-color: green;
    color: white;
    border: none;
  }
  </style>
  