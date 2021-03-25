<template>
  <Header/>
  <Todo/>
</template>

<script>
import Header from './components/Header.vue'
import Todo from './components/Todo.vue';

export default {
  name: 'App',
  components: {
    Header,
    Todo
  }
}
</script>

<style>
#app {
  font-family: Avenir, Arial, Helvetica, sans-serif;
}
</style>
