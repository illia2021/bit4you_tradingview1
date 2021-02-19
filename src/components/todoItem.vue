<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox" 
                   v-on:change="todo.completed = !todo.completed">
            <strong>{{index + 1}}</strong>
            {{todo.title}}
        </span>
        <button class="rm" 
                v-on:click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        },
        index: Number
    }
}
</script>

<style scoped>
    li {
        border: 1px solid #ccc;
        border-radius: 10px;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
        width: 250px;
    }
    .rm {
        background: red;
        color: #fff;
        border-radius: 50%;
        font-weight: bold;
        outline: none;
        border: none;
        cursor: pointer;
    }
    input {
        margin-right: 1rem;
        cursor: pointer;
    }
    .done {
        text-decoration: line-through;
    }

</style>