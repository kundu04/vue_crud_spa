<template>
<Header/>
<h1>Hello {{name}}! Welcome to Ecom</h1>
<table border="1">
    <tr class="heading">
        <td>Id</td>
        <td>Title</td>
        <td>Description</td>
        <td>Price</td>
        <td>Action</td>
    </tr>
    <tr v-for="item in products" :key="item.id">
        <td>{{item.id}}</td>
        <td>{{item.title}}</td>
        <td>{{item.description}}</td>
        <td>{{item.price}}</td>
        <td><router-link :to="'/update/'+item.id">Update</router-link>
        <button v-on:click="deleteProduct(item.id)">Delete</button>
        </td>
    </tr>
    
</table>
</template>
<script>
import axios from 'axios'
import Header from './Header.vue'
export default {
  components: { Header },
    name:'Home',
    data(){
        return{
            name:'',
            products:[]
        }
    },
    methods:{
        async deleteProduct(id){
            let result=await axios.delete("http://localhost:3000/products/"+id)
             if(result.status==200){
                this.loadProduct()
            }
        },

        async loadProduct(){
            let user = localStorage.getItem('user-info')
            if(!user){
                this.$router.push({name:'SignUp'})
            }
            this.name=JSON.parse(user).name

            let result=await axios.get("http://localhost:3000/products")
            this.products=result.data
            }
    },
    mounted(){
        this.loadProduct()
    }
}
</script>
<style >
td{
    width: 160px;
    height: 40px;
}
.heading{
    background-color:slategray;
    color:whitesmoke;
}
</style>