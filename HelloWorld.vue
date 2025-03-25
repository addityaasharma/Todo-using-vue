<script setup>
import { ref } from 'vue';

const newTask = ref('');
const tasks = ref([]);

const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value.trim());
    newTask.value = '';
  }
};

const removeTask = (index) => {
  tasks.value.splice(index, 1);
};
</script>

<template>
  <div class="flex flex-col items-center justify-center min-h-screen bg-gray-100">
    <!-- Todo List -->
    <div class="bg-white shadow-lg rounded-2xl p-8 w-full max-w-md">
      <h1 class="text-2xl font-bold text-center mb-6">Todo List</h1>
      <div class="flex items-center mb-4">
        <input 
          v-model="newTask" 
          @keyup.enter="addTask" 
          type="text" 
          placeholder="Enter your task" 
          class="w-full p-3 rounded-lg border border-gray-300 focus:outline-none focus:border-blue-500">
        <button 
          @click="addTask" 
          class="ml-2 p-3 bg-blue-500 text-white rounded-lg hover:bg-blue-600">
          Add
        </button>
      </div>
      <ul>
        <li 
          v-for="(task, index) in tasks" 
          :key="index" 
          class="flex justify-between items-center bg-gray-200 p-3 rounded-lg mb-2">
          <span>{{ task }}</span>
          <button 
            @click="removeTask(index)" 
            class="text-red-500 hover:text-red-700">
            Delete
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped></style>