<template>
    <div>
        <ul>
            <todoItem
            v-for="todo in todos"
            v-bind:todo="todo"
            :key="todo"
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
    }
}
</script>