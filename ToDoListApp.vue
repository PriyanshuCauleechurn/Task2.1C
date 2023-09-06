<script setup>

import { ref } from 'vue'

const header = ref('To Do List App')

const items = ref([

])

const newItem = ref("")
const newItemPriority = ref(false)
const saveItem = ()=>{
  items.value.push({id: items.value.length + 1, label: newItem.value, priority: newItemPriority.value})
  newItem.value = ""
  newItemPriority.value = ""
}
const editing = ref(false)
const doEdit = (e)=>{
  editing.value = e
  newItem.value = ""
  newItemPriority.value = ""
}
const toggleDone = (item)=>{
  item.done = !item.done
}
</script>


<template>
  <div class="header">
    <h1>{{ header }}</h1>
  </div>
  <button class="btn" v-if="editing" @click="doEdit(false)">Cancel Item</button>
  <button class="btn btn-primary" v-else @click="doEdit(true)">Add Item</button>
  <form class="addItemForm" v-if="editing" @submit.prevent="saveItem">
    <input v-model="newItem" type="text" placeholder="Add item">
    <label>
      <input type="checkbox" v-model="newItemPriority">High Priority
    </label>
    <button class="btn btn-primary" :disabled="newItem.length === 0">Save Item</button>
  </form>

  <ul>
    <li v-for="(item) in items" @click="toggleDone(item)" :key="item.id" class="static-class" :class="{strikeout: item.done, priority: item.priority}">
      {{ item.label }}">
    </li>
  </ul>

  <p v-if="!items.length">Nothing to do yet</p>
  
</template>
