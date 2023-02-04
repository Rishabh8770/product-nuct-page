<template>
  <div class="container-fluid">
      <div class="d-flex flex-wrap justify-content-around">
      <NuxtLink v-for="product in productList.products" :key="product.id"  class="product-card" :to="`/id/${product.id}`">
        <img :src="product.images?.[0]" alt="product image">
        <h5>{{product.title}}</h5>
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
            console.log(this.productList)
  }
}
</script>

<style>
  .product-card{
    border: 1px solid black;
    margin: 10px;
    width: 18rem;
    height: 22rem;
    border-radius: 10px;
    box-shadow: 5px 5px 5px 5px lightgray;
    text-decoration: none;
    color: black;
  }

  img{
    height: 17rem;
    width: 16.5rem;
    border: 1px solid black;
    margin: 10px;
    border-radius: 10px;

  }

  h5{
    text-align: center;
  }
</style>