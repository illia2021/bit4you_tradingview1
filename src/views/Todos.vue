<template>
  <div>
    <h2>Todo list</h2>
    <router-link to="/">Home</router-link>
    <hr>
    <addTodo 
        @add-todo="addTodo"
     />
     <hr>
     <select v-model="filter">
         <option value="all">All</option>
         <option value="completed">Completed</option>
         <option value="not-completed">Not completed</option>
     </select>
    <hr>
    <loader v-if="loading" />
    <todoList
        v-else-if="filteredTodos.length"
        v-bind:todos="filteredTodos"
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
      loading: true,
      filter: 'all'
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
//   watch: {
//       filter(value) {
//           console.log(value)
//       }
//   },
  computed: {
      filteredTodos() {
          if (this.filter === 'all') {
              return this.todos
          }
          if (this.filter === 'completed') {
              return this.todos.filter(t => t.completed)
          }
          if (this.filter === 'not-completed') {
              return this.todos.filter(t => !t.completed)
          }
      }
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