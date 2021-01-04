<template>
  <div>
      <h1>부모 컴포넌트에서 설정</h1>
      <p>{{ text }}</p>
      <button v-on:click="updatedText">Change Text</button>
    </div>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      default: 'ExampleText'
    }
  },

  methods: {
    updatedText() {
      this.$emit('updatedText',this.text);
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
