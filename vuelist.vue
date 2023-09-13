<script setup>
import { ref } from 'vue'

// give each todo a unique id
let id = 0

const newTodo = ref('')
const todos = ref([
  { id: id++, text: 'Learn HTML' },
  { id: id++, text: 'Learn JavaScript' },
  { id: id++, text: 'Learn Vue' }
])

function addTodo() {
  // ...
  todos.value.push({id: id++, text: newTodo.value})
  //adds new todo value from v-model="newTodo" input
  newTodo.value = ''
}

function removeTodo(todo) {
  // remove a specific todo item from the todos array
  //function takes one parameter, 'todo'. This parameter represents
  //the todo item that you want to remove from the todos array
  
  //the filter method is used to create a new array that includes only
  //the elements that meet a specific condition, in this case, it's used to
  // create a new array with all the todo items except the one that matches
  //the todo parameter 
  todos.value = todos.value.filter((t) => t != todo)
}
</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo">
    <button>Add Todo</button>    
  </form>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      <!--The click directive binds the removeTodo function to the buttons click event and passes the todo object associated with the current iteration of the v-loop as a parameter -->
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>
