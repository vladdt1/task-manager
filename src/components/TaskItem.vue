<template>
    <div :class="['task-item', { completed: task.completed }]">
      <input type="checkbox" v-model="task.completed" />
      <span>{{ task.text }}</span>
      <button @click="removeTask">Удалить</button>
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  
  const props = defineProps({
    task: Object,
  });
  
  const emit = defineEmits();
  
  const removeTask = () => {
    emit('remove', props.task.id);
  };
  </script>
  
  <style scoped>
  .task-item {
    display: flex;
    justify-content: space-between;
    padding: 10px;
    border-bottom: 1px solid #ccc;
  }
  
  .completed {
    text-decoration: line-through;
    color: gray;
  }
  
  button {
    background-color: red;
    color: white;
    border: none;
    padding: 5px;
  }
  </style>
  