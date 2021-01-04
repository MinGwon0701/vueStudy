<template>
    <div>
        <label for="">Name</label>
        <input 
            type="text" 
            v-bind:value="value"
            style="padding: 30px; border: 2px solid black;"
            @input="$emit('input', $event.target.value)"
        > 
        <br>
    </div>
</template>

<script>
export default {
    props: {
        value: {
            type: String,
            required: true,
        }
    },
    // methods: {
    //     updateName(e) {
    //         console.log(e.target.value);
    //         this.$emit('update-name', e);
    //     }
    // }
}
</script>