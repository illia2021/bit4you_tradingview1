<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit">Create</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit() {
            if(this.title.trim()) {
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false
                }

                this.$emit('add-todo', newTodo)
            }
        }
    }
}
</script>

<style scoped>
    form{
        width: 250px;
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
    }
    input{
        border-radius: 5px;
        border: 1px solid #333;
        outline: none;
    }
    button{
        color: #fff;
        border: none;
        border-radius: 5px;
        background: rgb(59, 25, 209);
        outline: none;
        cursor: pointer;
    }
    button:hover{
        color: rgb(43, 61, 226);
        background: #fff;
        border: 1px solid rgb(43, 61, 226);
    }
</style>