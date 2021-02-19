<template>
  <div>
    <h2>Todo list</h2>
    <router-link to="/">Home</router-link>
    <hr>
    <addTodo 
        @add-todo="addTodo"
     />
    <hr>
    <loader v-if="loading" />
    <todoList
        v-else-if="todos.length"
        v-bind:todos="todos"
        @remove-todo="removeTodo"
     />
     <p v-else>No todos!</p>
  </div>
</template>

<script>
import todoList from '@/components/todoList'
import addTodo from '@/components/addTodo'
import loader from '@/components/loader'
export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        setTimeout(() => {
            this.todos = json
            this.loading = false
        }, 1000)
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
    todoList, addTodo, loader
  }
}
</script>