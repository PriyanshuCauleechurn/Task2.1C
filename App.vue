<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <ToDoListApp msg="To Do List App"/>
</template>

<script>
import ToDoListApp from './components/ToDoListApp.vue';

export default {
  name: 'App',
  components: {
    ToDoListApp
  }
}
</script>