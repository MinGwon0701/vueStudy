<template>
  <div>
      <value-pass-no-3-ex :text.sync="text"/>

  </div>
</template>

<script>
import ValuePassNo3Ex from './ValuePassNo3Ex.vue'
export default {
    components: {
        ValuePassNo3Ex,
    },

    provide() {
        return {valuePassNo3: this};
    },

    data() {
        return {
            text: 'ExampleText',
        }
    },


}
</script>

<style>

</style>