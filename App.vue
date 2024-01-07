
<script setup>
import { ref } from 'vue';

// Reactive variables
const newTodo = ref('');
const todos = ref([
  { text: 'Learn Vue.js', completed: false },
  { text: 'Build a Vue app', completed: true },
]);

// Function to add a new todo
const addTodo = () => {
  if (newTodo.value.trim() !== '') {
    todos.value.push({ text: newTodo.value, completed: false });
    newTodo.value = ''; // Clear the input field after adding a todo
  }
};

// Function to remove a todo
const removeTodo = (index) => {
  todos.value.splice(index, 1);
};
</script>


<template>
  <div>
    <h1>Vue Todo List</h1>

    <!-- Form to add a new todo -->
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" placeholder="Add a new todo" />
      <button type="submit">Add Todo</button>
    </form>

    <!-- Display the list of todos -->
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <input type="checkbox" v-model="todo.completed" />
        <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
        <button @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
  </div>
  
</template>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>


