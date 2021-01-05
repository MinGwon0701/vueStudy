<template>
    <div>
        {{ setPage() }}
        
        <ul>
            <li>
                <button @click="pageMinus" v-if="startPage != 1"> &lt; </button>
            </li>

            <li v-for="index in pageCount" :key="index">
                <a href="#" @click="pageMove(index)" :style="startPage == index ? 'color: red; font-size: 20px;' : ''"> {{ index }} </a>
            </li>

            <li>
                <button @click="pagePlus" v-if="pageCount >= startPage  + pageRange"> &gt; </button>
            </li>
        </ul>
        
    </div>
</template>

<script>
export default {
    props: {
        firstList: Number,
        lastList: Number,
        listRange: Number,

        firstPage: Number,
        lastPage: Number,

        todoList: {
            value: Array,
            required: true
        }
    },

    data() {
        return {
            pageCount: 0,
            startPage: 1,
            nowPage: 1,
            endPage: 0,
            pageRange: 5,
            pageRange2: [1,2,3,4,5]
        }
    },

    methods: {
        setPage() {
            this.pageCount = Math.ceil(this.todoList.length / this.listRange);

            this.endPage = this.startPage + this.pageRange - 1;

            for(let i = this.startPage; i <= this.endPage; i++) {
                console.log(i);
            }

            console.group('---');
            console.log('endPage: ', this.endPage);
            console.log('nowPage: ', this.nowPage);
            console.log('pageCount: ', this.pageCount);
            console.log('startPage: ', this.startPage);
            console.groupEnd();
        },
        pageMinus() {
            this.startPage = this.startPage - this.pageRange;
            this.setPage();
        },
        pagePlus() {
            this.startPage = this.startPage +  this.pageRange;
            this.setPage();
        },
        pageMove(index) {
            this.nowPage = index;
            this.setPage();
        }
    },
}
</script>

<style scoped>
    a {
        text-decoration: none;
        color: black;
    }

    ul, ol {
        padding: 0;
        list-style: none;
        display: flex;
        align-items: baseline;
        justify-content: center;
    }

    li {
        margin: 0 5px;
    }
</style>