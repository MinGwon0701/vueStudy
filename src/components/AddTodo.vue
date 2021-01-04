<template>
  <div>
      <input 
        type="text" 
        placeholder="Type todo" 
        @keyup.enter="addTodo" 
        v-model="todoText"
      >
      {{ count }}
  </div>
</template>

<script>
export default {
    data() {
        return {
            todoText: '',
            todoText2: '',
            test: '',
            count: 0
        }
    },
    computed: {
        testCon() {
            return this.todoText + this.todoText2;
        }
    },
    watch: {
        testCon() {
            this.count++;
        }
    },
    methods: {
        addTodo() {
            this.$emit('add-todo', this.todoText);
            this.todoText = '';
        },
    }
}
</script>

<style>

</style>