<template>
    <div>
        <h1>자식 컴포넌트에서 설정1</h1>
        <p>{{text}}</p>
        <button v-on:click="updatedText">Change Text</button>
    </div>
</template>

<script>
export default {
   
   props: {
        text: {
            type: String,
            default: 'Example2'
        }
   },

   data() {
       return {
           text2: 'Example2'
       }
   },

   methods: {
       updatedText() {
           this.text2 = this.text2 + ' updated'
           this.$emit('update:text', this.text2)
       }
   },
}
</script>

<style scoped></style>