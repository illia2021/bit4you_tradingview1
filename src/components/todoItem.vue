<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox" 
                   v-on:change="todo.completed = !todo.completed">
            <strong>{{(index + 1) + '.'}}</strong>
            {{todo.title | uppercase}}
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
    },
    filters: {
        uppercase(value) {
            return value.toUpperCase()
        }
    }
}
</script>

<style scoped>
    span{
        display: flex;
        text-align: start;
        align-items: center;
    }
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
        height: 100%;
        align-self: center;
        
    }
    input {
        margin-right: 1rem;
        cursor: pointer;
    }
    strong{
        margin-right: 10px;
        align-self: center;
        font-size: 18px;
    }
    .done {
        text-decoration: line-through;
    }

</style>