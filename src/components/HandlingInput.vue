<template>
  <div>
    <h1>Handling Input</h1>
    <div>{{ msg }}</div>
    <button @click="reverseMsg">reverse</button>
    <button @click="msg += '!'">append "!"</button>
    <a href="https://vuejs.org" @click.prevent="notify"> A link with e.preventDefault()</a>
  </div>
</template>

<script setup>
import {ref} from "vue";

const msg = ref('Hello World!')
const reverseMsg = () => {
  msg.value = msg.value.split('').reverse().join('')
}
const notify = () => {
  alert('navigation was prevented.')
}
</script>

<style scoped>
</style>