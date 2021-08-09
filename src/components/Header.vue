<template>
    <div class="nav">
        <router-link to="/">Home</router-link>
        <router-link to="/add">Add Product</router-link>
        <a v-on:click="logout" href="">Logout</a>
    </div>
</template>
<script>
export default {
    name:'Header',

    methods:{
        logout(){
            localStorage.clear()
            this.$router.push({name:'Login'})
        }
    }
}
</script>
<style>
    .nav{
        background-color: slategray;
        overflow: hidden;
    }
    .nav a{
        float: left;
        color: white;
        text-align: center;
        padding: 20px 14px;
        text-decoration: none;
        font-size: 16px;
        margin-right: 4px;
    }
    .nav a:hover{
        background-color: wheat;
        color: black;
    }
</style>