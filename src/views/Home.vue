<template>
  <div>
    <h1>This Page is Home</h1>
    <form action="">
      <input-field v-model="value" />
      <button type="submit">Submit</button>
    </form>
    {{ value }}
  </div>
</template>

<script>
import InputField from '@/components/InputField.vue'

export default {
  components: {
    InputField
  },

  data() {
    return {
      count: 0,
      value: 'Kossie Coder',
      message: 'wow'
    }
  },

  computed: {
    computedCounter() {
      console.log('computed');
      return this.count;
    },
    reversedMessage() {
      return this.message.split('').reverse().join('');
    }
  }
}
</script>

<style scoped>
h1 {
  color: red;
}
</style>