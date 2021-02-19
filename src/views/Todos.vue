<template>
  <div>
    <h2>Todo list</h2>
    <router-link to="/">Home</router-link>
    <hr>
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
      todos: []
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