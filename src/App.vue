<template>
<router-view/>
</template>

<script>
export default {
  name: 'App',
 
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  padding: 0;
  margin: 0
}
.logo {
  height: 100px;
}

.register input ,.login input,.add input{
    height: 30px;
    width: 300px;
    padding-left: 20px;
    display: block;
    margin-bottom: 20px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid black;
}

.register button ,.login button,.add button{
    width: 320px;
    height: 30px;
    color: white;
    border: 1px solid black;
    background-color: black;
    cursor: pointer;
}
</style>
