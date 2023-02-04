<template>
  <div class="product-details d-flex justify-content-center">
    <img :src="details.images?.[0]" alt="prod-iamge" />
    <div class="details-container align-self-center">
        <h1>Details:</h1>
      <p>Model - {{ details.title }}</p>
      <p>Brand - {{details.brand}}</p>
      <p>About - {{ details.description }}</p>
      <p>Price - {{ details.price }}</p>
      <p>Rating - {{details.rating}}</p>
    </div>
  </div>
</template>



<script>
export default {
  async asyncData ({ params }) {
    // console.log("params", this.params)
    const details = await fetch(
      `https://dummyjson.com/products/${params.id}`
    ).then(res => res.json())
    // this.details = details
    // console.log('details', details)
    return { details }
  }
}
</script>

<style scoped>
    .product-details{
        margin: 5rem;
        border-radius: 10px;

    }

    img{
        width: 30%;
        height: 100%;
        padding: 10px;
        border: 2px solid red;
        border-radius: 10px;
    }

    .details-container{
        margin: 10px;
    }
</style>

<!-- details {
  id: 3,
  title: 'Samsung Universe 9',
  description: "Samsung's new variant which goes beyond Galaxy to the Universe",
  price: 1249,
  discountPercentage: 15.46,
  rating: 4.09,
  stock: 36,
  brand: 'Samsung',
  category: 'smartphones',
  thumbnail: 'https://i.dummyjson.com/data/products/3/thumbnail.jpg',
  images: [ 'https://i.dummyjson.com/data/products/3/1.jpg' ]
} -->
