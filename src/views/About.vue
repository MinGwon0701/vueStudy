<template>
  <div class="about">
    <h1>This Page is About</h1>
    <kossie-coder v-on:updatedInfo="updatedInfo" v-bind:name="name">
      <template #subName="{ maximum, minimum }">
        <div>
          maximum: {{ maximum }} <br>
          minimum: {{ minimum }}
        </div>
      </template>
    </kossie-coder>
  </div>
</template>

<script>
import KossieCoder from '../components/KossieCoder.vue';

export default {
  components: {
    KossieCoder,
  },

  data() {
    return {
      name: 'default name',
      count: 2,
      todoText: '',
      todos: [
        { id: 1, text: 'buy a car', checked: false },
        { id: 2, text: 'play game', checked: false },
      ]
    }
  },

  methods: {
    updatedInfo() {},
    addTodo(todoText) {
      this.count++;
      this.todos.push({
        id: this.count,
        text: todoText,
        checked: false
      });
      console.log(this.todos); 
      this.todoText = '';
    },
    toggleCheckbox({id,checked}) {
      const index = this.todos.findIndex(todo => {
        return todo.id === id;
      });
      this.todos[index].checked = checked;
    },
    deleteTodo(id) {
      // const index = this.todos.findIndex(todo => {
      //   return todo.id === id;
      // });
      // this.todos.splice(index, 1);
      this.todos = this.todos.filter(todo => todo.id !== id);
      console.log(this.todos); 
    }
  },
}
</script>