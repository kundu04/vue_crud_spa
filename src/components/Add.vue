<template>
<Header/>
<h1>Add Product</h1>
<form class="add">
  <input type="text" placeholder="Enter title" name="title" v-model="product.title">
  <input type="text" placeholder="Enter description" name="description\" v-model="product.description">
  <input type="number" placeholder="Enter price" name="price" v-model="product.price">
  <button type="button" v-on:click="addProduct">Add Product</button>
</form>
</template>
<script>
import axios from 'axios'
import Header from './Header.vue';
export default {
  components: { Header },
    name:'Add',
    data(){
      return{
        product:{
          title:'',
          description:'',
          price:''
        }
          
      }
    },
    methods:{
      async addProduct(){
         const result=await axios.post("http://localhost:3000/products",{
                title:this.product.title,
                description:this.product.description,
                price:this.product.price
                });
            if(result.status==201){
                this.$router.push({name:'Home'})
            } 
      }
    },
    mounted(){
        let user = localStorage.getItem('user-info');
        if(!user){
            this.$router.push({name:'SignUp'})
        }
    }
}
</script>