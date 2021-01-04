<template>
  <div>
      <value-pass-no-2-ex :text.sync="text" @update:text="updatedText"/>
  </div>
</template>

<script>
import ValuePassNo2Ex from './ValuePassNo2Ex.vue'
export default {
    components: {
        ValuePassNo2Ex,
    },

    data() {
        return {
            text: 'ExampleText',
        }
    },

    methods: {
        updatedText(text) {
            this.text = text;
        }
    },
}
</script>

<style>

</style>