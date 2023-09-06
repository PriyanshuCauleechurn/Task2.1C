<script setup>

import { ref } from 'vue'

const header = ref('Vue 3 concepts')

const ifText = ref(true)

const showElement = ref(false)

const fruits = ref([
  {id: 1, label: "banana"},
  {id: 2, label: "apple"},
  {id: 3, label:"pear"}
])

</script>

<template>

  <div class="header">
    <h1>{{ header }}</h1>
  </div>

  <div id="app">
    <h3>Using v-if and v-else</h3>
    <p v-if="ifText">This text will only appear if ifText is true.</p>
    <p v-else>Else if ifText is false you will see this alert</p>
    <button @click="ifText = !ifText">Toggle Text</button>
</div>

<div id="app">
  <h3>Using v-show</h3>
  <p>Right now nothing can be seen on the screen since showElemnt is false</p>
  <button @click="showElement = !showElement">Click to change showElement</button>
  <p v-show="showElement">This is a Vue 3 v-show Example</p>
</div>

<div id="app">
  <h3>Using v-for</h3>
  <p>Right now the list that is rendering on the screen is stored in an array and we are using v-for to display each item inside the array</p>
  <ul>
    <li v-for="fruit in fruits" :key="fruit.id">{{ fruit.label }}</li>
  </ul>
</div>

<div id="app">
  <h3>Using v-for and v-if</h3>
  <ul>
    <li v-for="fruit in fruits" :key="fruit.id">
      <span v-if="fruit.id === 1"> This is a yellow fruit</span>
      <span v-else-if=" fruit.id === 2"> This is a red fruit</span>
      <span v-else> This is a green fruit</span>
    </li>
  </ul>
</div>

</template>