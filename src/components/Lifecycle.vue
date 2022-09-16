<script setup>
import {defineEmits, onMounted, ref, watch} from 'vue'
import Slots from "@/components/Slots";

const p = ref(null)

onMounted(() => {
  p.value.textContent = 'mounted!'
})
//
const todoId = ref(1)
const todoData = ref(null)

async function fetchData(text) {
  console.log(text)
  todoData.value = null
  const res = await fetch(
      `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
  )
  todoData.value = await res.json()
}

onMounted(() => fetchData('onMounted'))
fetchData('method')
watch(todoId, fetchData)

const count = ref(0)

watch(count, (newCount) => {
  console.log(`new count is: ${newCount}`)
})
const emit = defineEmits(['responseEmit', 'emitTwo'])
emit('responseEmit', 'emit!!')
emit('emitTwo', 'emitTwo!!')
const msgRef = ref("slot ref")
const msgConst = ref("slot const")
</script>

<template>
  <p ref="p">hello</p>
  {{ count }}
  <div>
    <p>To do is : {{ todoId }}</p>
    <button @click="todoId++">Fetch next todo</button>
    <p v-if="!todoData">Loading...</p>
    <pre v-else>{{ todoData }}</pre>
  </div>
  <Slots>{{ msgRef }}</Slots>
  <Slots>{{ msgConst }}</Slots>
</template>
