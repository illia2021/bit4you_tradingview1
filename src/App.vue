<template>
  <div id="app">
    <h1>Todo application</h1>
    <addTodo 
        @add-todo="addTodo"
     />
    <hr>
    <todoList
        v-bind:todos="todos"
        @remove-todo="removeTodo"
     />
  </div>
</template>

<script>
import todoList from '@/components/todoList'
import addTodo from '@/components/addTodo'
export default {
  name: 'App',
  data() {
    return {
      todos: [
        // {id: 1, title: 'Buy a loaf of bread', completed: false},
        // {id: 2, title: 'Buy a book', completed: false},
        // {id: 3, title: 'Buy a butter', completed: false}
      ]
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        this.todos = json
      })
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  components: {
    todoList, addTodo
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
