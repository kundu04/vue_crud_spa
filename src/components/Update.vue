<template>
<Header/>
<h1>Update page</h1>
<form class="add">
  <input type="text" placeholder="Enter title" name="title" v-model="product.title">
  <input type="text" placeholder="Enter description" name="description\" v-model="product.description">
  <input type="number" placeholder="Enter price" name="price" v-model="product.price">
  <button type="button" v-on:click="updateProduct">Update Product</button>
</form>
</template>
<script>
import axios from 'axios'
import Header from './Header.vue';
export default {
  components: { Header },
    name:'Update',
   
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
      async updateProduct(){
         const result=await axios.put("http://localhost:3000/products/"+this.$route.params.id,{
                title:this.product.title,
                description:this.product.description,
                price:this.product.price
                });
            if(result.status==200){
                this.$router.push({name:'Home'})  
            } 

      }
    },
    async mounted(){
        let user = localStorage.getItem('user-info');
        if(!user){
            this.$router.push({name:'SignUp'})
        }
        const result=await axios.get("http://localhost:3000/products/"+this.$route.params.id)
        this.product=result.data
    }
}
</script>