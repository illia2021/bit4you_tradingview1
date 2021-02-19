<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit">create</button>
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
                this.title = ''
            }
        }
    }
}
</script>

<style scoped>
    form{
        width: 300px;
        margin: 0 auto;
        display: flex;
        justify-content: space-around;
    }
    input{
        border-radius: 5px;
        border: 1px solid #333;
        outline: none;
        height: 25px;
    }
    button{
        color: #fff;
        border: none;
        border-radius: 5px;
        background: rgb(59, 25, 209);
        outline: none;
        cursor: pointer;
        width: 70px;
        font-size: 15px;
        font-weight: bold;
    }
    button:hover{
        color: rgb(43, 61, 226);
        background: #fff;
        border: 1px solid rgb(43, 61, 226);
    }
</style>