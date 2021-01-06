<template>
    <div>
        <ul>
            <li v-if="startPage != 1">
              <button @click="pageMinus"> &lt; </button>
            </li>
            <li v-for="index in pageCount" :key="index">
               <a href="#" @click="pageClick(index)" :style="index == nowPage ? 'color: red; font-size: 20px;' : ''"> {{ index }} </a>
            </li>
            <li v-if="endPage != pageCount">
               <button @click="pagePlus"> &gt; </button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        todoList: {
            value: Array,
            required: true,
        },

        startList: Number,
        lastList: Number,
        listRange: Number,

        // firstPage: Number,
        pageCount: Number,
        startPage: Number,
        nowPage: Number,
        endPage: Number,
        pageRange: Number,


    },

    methods: {
        pageMinus() {
            this.$emit('pageMinus');
        },
        pageClick(index) {
            this.$emit('pageClick',index);
        },
        pagePlus() {
            this.$emit('pagePlus');
        },
    },
}
</script>

<style scoped>
ul {
    list-style: none;
    display: flex;
    align-items: baseline;
    justify-content: center;
}
a {
    text-decoration: none;
    color: black;
    margin: 0 5px;
}
button {
    cursor: pointer;
}
</style>