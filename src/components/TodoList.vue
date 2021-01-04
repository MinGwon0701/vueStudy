<template>
    <div>
        <input type="checkbox" :checked="todoItem.checked" @change="toggleCheckbox(todoItem.index)"> 
        <!-- {{ todoItem.index }} | -->
        <span :style="todoItem.checked ? 'text-decoration: line-through; text-decoration-color: red;': ''">{{ todoItem.text }} </span>
        <!-- {{ todoItem.checked }}  -->
        <button @click="deleteTodo(todoItem.index)">Delete</button>
    </div>
</template>

<script>
export default {
    props: {
        todoItem: {
            value: Object,
            required: true
        }
    },
    methods: {
        deleteTodo(index) {
            this.$emit('deleteTodo', index);
        },

        toggleCheckbox(index) {
            this.$emit('toggleCheckbox', index);
        }
    },
}
</script>

<style scoped>

</style>