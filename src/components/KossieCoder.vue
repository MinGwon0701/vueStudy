<template>
    <div>
        <h1>{{ title }}</h1>
        <p>{{ name }}</p>
        <slot name="subName" v-bind:maximum="maximum" v-bind:minimum="minimum">sub name</slot>
        <button v-on:click="updatedInfo">Change Name</button>
        <slot name="info">default info</slot>
    </div>
</template>

<script>
export default {
    props: {
        title: {
            type: String,
            default: 'default title'
        },
        name: {
            type: String,
            default: 'default name222'
        },
    },
    data() {
        return {
            maximum: 999,
            minimum: 0
        }
    },
    methods: {
        updatedInfo() {
            this.$emit('updatedInfo', this.name);
        },
    }
}
</script>

<style scoped>

</style>