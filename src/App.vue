<template>
  <div id="app">
    <h1>todo application</h1>
    <hr>
    <todoList
    v-bind:todos="todos"
     />
  </div>
</template>

<script>
import todoList from '@/components/todoList'
export default {
  name: 'App',
  data() {
    return {
      todos: [
        {id: 1, title: 'buy a loaf of bread', completed: false},
        {id: 2, title: 'buy a book', completed: false},
        {id: 3, title: 'buy a butter', completed: false}
      ]
    }
  },
  components: {
    todoList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
