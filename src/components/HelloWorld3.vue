<template>
    <div>
        <h1>자식 컴포넌트에서 설정2</h1>
        <p>{{text}}</p>
        <button v-on:click="updatedText">Changed Text</button>
    </div>
</template>

<script>
export default {

    props: {
        text: {
            type: String,
            default: 'Example'
        }
    },
    inject: {
        example: {
            default: null
        }
    },
    methods: {
        updatedText() {
            this.example.text3 = this.text + ' wow';
            console.log('this.example.text3: ', this.example.text3);
        }
    },
}
</script>

<style lang="stylus" scoped>

</style>