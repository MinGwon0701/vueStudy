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
            :pageCount="pageCount"
            :startPage="startPage"
            :nowPage="nowPage"
            :endPage="endPage"
            :pageRange="pageRange"
            @pageMinus="pageMinus"
            @pageClick="pageClick"
            @pagePlus="pagePlus"
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

            startList: 0,
            lastList: 0,
            listRange: 5,

            // firstPage: Number,
            pageCount: 0,
            startPage: 1,
            nowPage: 1,
            endPage: 0,
            pageRange: 5,
        }
    },

    created() {
        for(let i = 0; i < 150 ; i++){
            this.todoList.push({
                text: 'test',
                index: this.count,
                checked: false,
            });
            this.count++;
        }
        
        this.pageCount = Math.ceil(this.todoList.length / this.listRange);
    },

    methods: {
        insertTodo(event) {
            this.todoList.push({
                text: event.target.value,
                index: this.count,
                checked: false,
            });
            this.count++;
            console.log(this.todoList);
            this.text ='';

            this.todoPaging();
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
            this.todoPaging();
        },
        completedCountCon() {
            this.completedCount = 0;

            this.todoList.forEach(todo => {
                if(todo.checked == true)
                    this.completedCount++;
            });
        },
        todoPaging() {
            this.pageCount = Math.ceil(this.todoList.length / this.listRange);


        },
        pageMinus() {
            let index = this.nowPage - 5;
            // this.nowPage -= 5;
            this.endPage = Math.floor(index / 5 + 1) * 5;

            // 5, 10, 15, 20, 25... 일 때, 따로 실행
            if(index % 5 == 0) {
                this.endPage = Math.floor(index / 5) * 5;
            }

            this.startPage = this.endPage - 4;
            this.nowPage = this.startPage;

            if(this.endPage > this.pageCount) {
                this.endPage = this.pageCount;
            }
        },
        pageClick(index) {
            this.nowPage = index;
            
            this.endPage = (Math.floor(index / 5) + 1) * 5;

            // 5, 10, 15, 20, 25... 일 때, 따로 실행
            if(index % 5 == 0) {
                this.endPage = Math.floor(index / 5) * 5;
            }

            this.startPage = this.endPage - 4;

            if(this.endPage > this.pageCount) {
                this.endPage = this.pageCount;
            }
        },
        pagePlus() {
            let index = this.nowPage + 5;
            // this.nowPage += 5;
            this.endPage = Math.floor(index / 5 + 1) * 5;

            // 5, 10, 15, 20, 25... 일 때, 따로 실행
            if(index % 5 == 0) {
                this.endPage = Math.floor(index / 5) * 5;
            }

            this.startPage = this.endPage - 4;
            this.nowPage = this.startPage;

            if(this.endPage > this.pageCount) {
                this.endPage = this.pageCount;
            }
        },
    },
}
</script>

<style scoped>

</style>