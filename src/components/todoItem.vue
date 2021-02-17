<template>
    <li>
        <span>
            <input type="checkbox">
            <strong>{{todo.id}}</strong>
            {{todo.title}}
        </span>
        <button class="rm">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
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
    }
    input {
        margin-right: 1rem;
    }
    .done {
        text-decoration: line-through;
    }

</style>