<template>
  <div>
    <ol>
      <ChildComponent v-for="item in groceryList" :key="item.id" :todo="item"></ChildComponent>
    </ol>
  </div>
</template>

<script setup>
import {ref} from "vue";
import ChildComponent from "@/components/ChildComponent";


const groceryList = ref([
  {id: 0, text: 'Vegetables'},
  {id: 1, text: 'Cheese'},
  {id: 2, text: 'Whatever'},
])
</script>

<style scoped>

</style>