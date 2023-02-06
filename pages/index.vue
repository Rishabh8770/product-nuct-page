<template>
  <div class="container-fluid">
      <div class="d-flex flex-wrap justify-content-around bg-light">
      <NuxtLink v-for="product in productList.products" :key="product.id"  class="product-card" :to="`/id/${product.id}`">
        <img :src="product.images?.[0]" alt="product image">
        <p class="prod-title">{{product.title}}</p>
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data(){
    return{
      productList:[],
    }
  },

  async mounted(){
    this.productList = await fetch('https://dummyjson.com/products')
            .then(res => res.json())
  }
}
</script>

<style>
  .product-card{
    border: 1px solid black;
    margin: 10px;
    width: 12rem;
    height: auto;
    border-radius: 10px;
    box-shadow: 0px 0px 10px 4px lightgray;
    text-decoration: none;
    color:purple;
  }

  .product-card:hover{
    -ms-transform: scale(1.1); /* IE 9 */
  -webkit-transform: scale(1.5); /* Safari 3-8 */
  transform: scale(1.1);
  }

  img{
    height: 11rem;
    width: 10.5rem;
    border: 1px solid black;
    margin: 10px;
    border-radius: 10px;

  }

  .prod-title{
    text-align: center;
    padding: 3px;

  }

 
</style>