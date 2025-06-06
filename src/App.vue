<script setup>
import { ref } from 'vue';

const name = ref('Josh Cagara');
const status = ref('active');
const tasks = ref(['One', 'Two', 'Three']);
const newTask = ref('Enter Task');

//declaring a method in view
const toggleStatus = () => {
    if (status.value === 'active'){
      status.value = 'pending';
    }else if (status.value === 'pending'){
      status.value = 'inactive';
    }else{
      status.value = 'active';
    }
};

const addTask = () => {
  if(newTask.value.trim() !== ''){
    tasks.value.push(newTask.value);
    newTask.value = '';
  }

}
</script>

<template>
  <h1>Practice Vue</h1>
  <p v-if="status === 'active'"> User is Active</p>
  <p v-else-if="status === 'pending'"> User is Pending</p>
  <p v-else="status === 'inactive'"> User is Inactive</p>

  <button @click="toggleStatus">Change status</button>
  <br>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task </label>
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <br>
    <button type="submit">Add</button>
  </form>
  <h3>Task:</h3>
  <ul>
    <li v-for="task in tasks" :key="task"> {{ task }}</li>
  </ul>
</template>