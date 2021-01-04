<template>
  <div>
      <value-pass-no-1-ex @updatedText="updatedText" :text="text"/>
  </div>
</template>

<script>
import ValuePassNo1Ex from './ValuePassNo1Ex.vue';
export default {
    components: { 
        ValuePassNo1Ex,
    },

    data() {
        return {
            text: 'ExampleText',
        }
    },
    
    methods: {
        updatedText() {
            this.text += ' plus';
        }
    },

}
</script>

<style scoped>
</style>