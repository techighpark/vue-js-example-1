<template>
  <div>
    <h1>Attribute Bindings</h1>
    <p>
      <span :title="msg">Hover your mouse over me</span>
    </p>
    <p :class="{red :isRed}" @click="toggleRed">This should be red. but click me to toggle it</p>
    <p :style="{color}" @click="toggleColor">This should be green, and should toggle between green and blue on
      click.</p>

  </div>
</template>

<script setup>
import {ref} from "vue";

const msg = ref('Hello World!')
const isRed = ref(true)
const color = ref('green')

const toggleRed = () => {
  isRed.value = !isRed.value
}
const toggleColor = () => {
  color.value = color.value === 'green' ? 'blue' : 'green'
}
</script>

<style scoped>
.red {
  color: red
}
</style>