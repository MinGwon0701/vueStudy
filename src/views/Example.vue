<template>
    <div>
        <router-link to="/example/valuePass">컴포넌트 간 데이터 다루기</router-link>
        <br> <br>
        <router-link to="/example/Todo">Todo</router-link>
        
        <!-- <router-view/> -->
    </div>
</template>

<script>
export default {

}
</script>

<style scoped>
    a {
        font-weight: bold;
        color: #2c3e50;
    }

    #nav a.router-link-exact-active {
        color: #42b983;
    }
</style>