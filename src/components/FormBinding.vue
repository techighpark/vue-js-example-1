<template>
  <div>
    <h1>Form Binding</h1>
    <h3>Text Input</h3>
    <input v-model="text">{{ text }}
    <h3>Check Box</h3>
    <input id="checkbox" v-model="checked" type="checkbox">
    <label for="checkbox">Checked : {{ checked }}</label>

    <!--    multiple checkboxes can bind to the same array v-model values-->
    <h3>Multi Checkbox</h3>
    <input id="jack" v-model="checkedName" type="checkbox" value="Jack">
    <label for="jack"></label>
    <input id="john" v-model="checkedName" type="checkbox" value="John">
    <label for="john"></label>
    <input id="mike" v-model="checkedName" type="checkbox" value="Mike">
    <label for="mike"></label>
    <p>Checked name : <pre>{{checkedName}}</pre></p>
    <p>Checked name : <pre>{{checkedNameR}}</pre></p>
  </div>

  <h2>Radio</h2>
  <input type="radio" id="one" value="One" v-model="picked">
  <label for="one">One</label>
  <br>
  <input type="radio" id="two" value="Two" v-model="picked">
  <label for="two">Two</label>
  <br>
  <span>Picked: {{ picked }}</span>

  <h2>Select</h2>
  <select v-model="selected">
    <option disabled value="">Please select one</option>
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <span>Selected: {{ selected }}</span>

  <h2>Multi Select</h2>
  <select v-model="multiSelected" multiple style="width:100px">
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <span>Selected: {{ multiSelected }}</span>
</template>

<script setup>
  import {reactive, ref} from "vue";

  const text = ref('Edit me')
  const checked = ref(true)
  const checkedName = ref(['Jack'])
  const checkedNameR = reactive(['Jack'])
  const picked = ref('One')
  const selected = ref('A')
  const multiSelected = ref(['A'])
</script>

<style scoped>

</style>