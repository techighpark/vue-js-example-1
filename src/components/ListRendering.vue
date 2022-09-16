<template>
  <form @submit.prevent="addTodo">
    <input v-model="newToDo">
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in todos" :key="todo.id">{{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>

<script setup>
import {reactive, ref} from 'vue'

let id = 0;
const newToDo = ref('')
const newToDoR = reactive({value: ''})
const todos = ref([
  {id: id++, text: "Learn HTML"},
  {id: id++, text: "Learn JavaScript"},
  {id: id++, text: "Learn Vue"}
])
const todosR = reactive([
  {id: id++, text: "Learn HTML"},
  {id: id++, text: "Learn JavaScript"},
  {id: id++, text: "Learn Vue"}
])

function addTodo() {
  todos.value.push({id: id++, text: newToDo.value})
  newToDo.value = ''
  console.log(newToDo)
  console.log(newToDo.value)
  console.log(newToDoR)
  console.log(newToDoR.value)
  console.log(todos)
  console.log(todos.value)
  console.log(todosR)
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}

</script>
<style scoped>

</style>