<template>
  <div>
        <h1>자식 컴포넌트에서 데이터 바꾸기2</h1>
        <p>{{ text }}</p>
        <button @click="updatedText">Changed Text</button>
  </div>
</template>

<script>
export default {
    props: {
        text: {
            value: String, 
            default: 'ExampleText'
        }
    },

    inject: {
        valuePassNo3: {
            default: null,
        }
    },

    methods: {
        updatedText() {
            this.valuePassNo3.text = this.text + ' updated';
        }
    },
}
</script>

<style>

</style>