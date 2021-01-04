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
    <br>
    <div>
      <h1>Todo App</h1>

      <completed-todo v-bind:todos="todos"/>

      <add-todo v-on:add-todo="addTodo"/>
      
      <todo-list
        v-bind:todos="todos" 
        v-on:toggle-checkbox="toggleCheckbox"
        v-on:click-delete="deleteTodo"
      />
    </div>
    
  </div>
</template>

<script>
import AddTodo from '../components/AddTodo.vue';
import CompletedTodo from '../components/CompletedTodo.vue';
import KossieCoder from '../components/KossieCoder.vue';
import TodoList from '../components/TodoList.vue';

export default {
  components: {
    KossieCoder,
    AddTodo,
    TodoList,
    CompletedTodo
  },

  data() {
    return {
      name: 'default name',
      count: 3,
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