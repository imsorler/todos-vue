<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="newTitle">
        <button type="submit">Create</button>
    </form>
</template>

<script>

export default {
    data() {
        return {
            newTitle: ''
        }
    },
    methods: {
        onSubmit() {
            if(this.newTitle.trim()) {
                const newTodo = {
                    id: Date.now(),
                    title: this.newTitle,
                    completed: false
                }

                this.$emit('add-todo', newTodo)
                this.newTitle = ''
            }
        }
    }
}

</script>

<style scoped>
    form {
        display: flex;
    }

    input {
        width: 400px;
    }
</style>