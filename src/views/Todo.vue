<template>
    <div>
        completedCount: {{ completedCount }} <br>

        <input type="text" @keyup.enter="insertTodo" :value="text"> <br>
        
        <todo-list
            v-for="todoItem in todoList"
            :key="todoItem.index" 
            :todoItem="todoItem"
            @deleteTodo="deleteTodo"
            @toggleCheckbox="toggleCheckbox"
        />

        <todo-paging
            :todoList="todoList"
        />
    </div>
</template>

<script>
import TodoList from '../components/TodoList.vue'
import TodoPaging from '../components/TodoPaging.vue'
export default {
    components: {
        TodoList,
        TodoPaging,
    },

    data() {
        return {
            todoList: [{
                index: 0,
                text: '하하',
                checked: false
            }],
            text: '',
            count: 1,
            completedCount: 0,
        }
    },

    methods: {
        insertTodo(event) {
            for(let wow = 0; wow < 30 ; wow++){ //데이터 생산을 위해 만듬 끝나면 지우세요
                this.todoList.push({
                    text: event.target.value,
                    index: this.count,
                    checked: false,
                });
                this.count++;
                console.log(this.todoList);
                this.text ='';
            }
            
        },
        toggleCheckbox(index) {
            let index2 = this.todoList.findIndex(todo => todo.index == index);
            this.todoList[index2].checked = !this.todoList[index2].checked;

            this.completedCountCon();
        },
        deleteTodo(index) {
            this.todoList = this.todoList.filter(todo => todo.index != index);
            console.log(this.todoList);

            this.completedCountCon();
        },
        completedCountCon() {
            this.completedCount = 0;

            this.todoList.forEach(todo => {
                if(todo.checked == true)
                    this.completedCount++;
            });
        }
    },
}
</script>

<style scoped>
</style>