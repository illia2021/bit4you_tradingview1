<template>
    <div>
        <ul>
            <todoItem
            v-for="(todo, i) in todos"
            v-bind:todo="todo"
            v-bind:index="i"
            :key="todo"
            v-on:remove-todo="removeTodo"
            />
        </ul>
    </div>
</template>

<script>
import todoItem from '@/components/todoItem'
export default {
    props: ['todos'],
    components: {
        todoItem
    },
    methods: {
        removeTodo(id) {
            this.$emit('remove-todo', id)
        }
    }
}
</script>

<style scoped>
    ul {
        list-style: none;
        margin: 0 auto;
        padding: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
</style>