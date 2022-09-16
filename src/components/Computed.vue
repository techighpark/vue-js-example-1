<template>
  methods: {{ methodsFn() }}
  <div></div>
  computed: {{ computedFn }}


  <form @submit.prevent="addTodo">
    <input v-model="newTodo"/>
    <button>Add Todo</button>
  </form>
  {{ filteredTodos }}
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input v-model="todo.done" type="checkbox">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>

  <Lifecycle/>

</template>

<script setup>
import {computed, ref} from 'vue'
import Lifecycle from "@/components/Lifecycle";

let id = 0
const newTodo = ref('')
const hideCompleted = ref(false)
const todos = ref([
  {id: id++, text: 'Learn HTML', done: true},
  {id: id++, text: 'Learn JavaScript', done: true},
  {id: id++, text: 'Learn Vue', done: false}
])

const filteredTodos = computed(() => {
  return hideCompleted.value
      ? todos.value.filter((t) => !t.done)
      : todos.value
})

function addTodo() {
  todos.value.push({id: id++, text: newTodo.value, done: false})
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}

function methodsFn() {
  return new Date();
}

const computedFn = computed(() => {
  return new Date();
})
</script>


<style>
.done {
  text-decoration: line-through;
}
</style>