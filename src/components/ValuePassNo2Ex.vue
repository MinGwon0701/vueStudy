<template>
  <div>
      <h1>자식 컴포넌트에서 데이터 바꾸기</h1>
      <p>{{ text }}</p>
      <button @click="updatedText">Changed Text</button>

  </div>
</template>

<script>
export default {
    props: {
        text: {
            value: String,
            defaulr: "ExampleText"
        }
    },

    data() {
        return {
            exampleText: 'ExampleText',
        }
    },

    methods: {
        updatedText() {
            this.exampleText += ' updated';
            this.$emit('update:text', this.exampleText);
        }
    },
}
</script>

<style>

</style>