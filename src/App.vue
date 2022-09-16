<template>
  <div>
    <LifeCycleTest/>
  </div>
  <div v-if="false">
    <ParentComponent/>
    <FormBinding/>
    <AttributeBindings/>
    <HandlingInput/>
    <h1>{{ msg }}</h1>
    <p>{{ counter.count }}</p>
    <p>{{ number }}</p>
    <div :id="titleClass">dynamic class or dynamic id</div>
    <button @click="increment">{{ counter.count }}</button>
    <!--    same with bottom html-->
    <div>
      <input :value="text" @input="onInput">
      {{ text }}
    </div>
    <!--    same with above html-->
    <div>
      <input v-model="textModel">
      {{ textModel }}
    </div>
    <ListRendering/>
    <Computed/>
  </div>
</template>


<script setup>
import {reactive, ref} from "vue";
import ListRendering from "@/components/ListRendering";
import Computed from "@/components/Computed";
import HandlingInput from "@/components/HandlingInput";
import AttributeBindings from "@/components/AttributeBindings";
import FormBinding from "@/components/FormBinding";
import ParentComponent from "@/components/ParentComponent";
import LifeCycleTest from "@/components/LifeCycleTest";

const counter = reactive({count: 0})
const number = ref(0)
const msg = ref('Hello World')
const titleClass = ref('title')
const text = ref('')
const textModel = ref('')

msg.value = 'changed'

function increment() {
  counter.count++


  number.value++
}

function onInput(e) {
  text.value = e.target.value
}


</script>

<style>
#title {
  color: red
}

</style>
