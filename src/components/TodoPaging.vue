<template>
  <div>
      <ul>
          <li><button> &lt; </button></li>
          <li v-for="index in 5" :key="index">
              <a href="#">{{ index }}</a>
          </li>
          <li><button> &gt; </button></li>
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


}
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
}
</style>