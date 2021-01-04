<template>
  <div>
      <h1>부모 컴포넌트에서 데이터 바꾸기</h1>
      <p>{{ text }}</p>
      <button @click="updatedText">Changed Text</button>
  </div>
</template>

<script>
export default {
    props: {
        text: {
            value: String,
            default: "ExampleText"
        }
    },

    methods: {
        updatedText() {
            this.$emit('updatedText', this.text);
        }
    },
}
</script>

<style>

</style>