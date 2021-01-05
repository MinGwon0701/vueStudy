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

        <todo-page-con 
            :todoList="todoList"
            :listRange="listRange"
        />
    </div>
</template>

<script>
import TodoPageCon from '../components/TodoPageCon.vue'
import TodoList from '../components/TodoList.vue'
export default {
    components: {
        TodoList,
        TodoPageCon,
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

            firstList: 0,
            lastList: 0,
            listRange: 5,

            pageCount: 0,
            firstPage: 0,
            nowPage: 0,
            lastPage: 0,
            startPage: 0,
            endPage: 0,
            pageRange1: 0,
            pageRange2: 0,
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