<template>
    <div>
        <!-- 부모 컴포넌트에서 데이터 바꾸기 -->
        <value-pass-no-1 /> <br> <hr>

        <!-- 자식 컴포넌트에서 데이터 바꾸기 -->
        <value-pass-no-2 /> <br> <hr>
        <value-pass-no-3 /> <br> <hr>
  </div>
</template>

<script>
import ValuePassNo1 from '../components/ValuePassNo1.vue';
import ValuePassNo2 from '../components/ValuePassNo2.vue';
import ValuePassNo3 from '../components/ValuePassNo3.vue';

export default {
    components: { 
        ValuePassNo1,
        ValuePassNo2,
        ValuePassNo3,
    },
}
// 
</script>

<style scoped>
</style>