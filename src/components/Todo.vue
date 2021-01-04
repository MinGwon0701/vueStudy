<template>
    <div>
        <input type="checkbox" :checked="todo.checked" @change="toggleCheckbox">
        <span 
        :style="todo.checked ? 'text-decoration: line-through' : ''">
            {{ todo.text }}
        </span>

        <button @click="clickDelete">Delete</button>
    </div>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
    },
    methods: {
        toggleCheckbox(e) {
            this.$emit('toggle-checkbox', {
                id: this.todo.id,
                checked: e.target.checked
            });
        },
        clickDelete() {
            this.$emit('click-delete', this.todo.id)
        }
    },
}
</script>

<style scoped>

</style>