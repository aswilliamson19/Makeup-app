<template lang="html">
  <div v-if="product" id="product-detail">
    <h3>{{ product.name }}, made by {{ product.brand }}</h3>
    <p>{{ product. type }}</p>
    <p>{{ product.description }}</p>
    <label for="buy-button">You can buy {{ product.name }} here: </label>
    <button v-on:click="goToSite(product.product_link)"  name="link-button">Shop for product!</button><br>
    <button v-if="!favouriteProducts.includes(product)" v-on:click="addToFavourites">Add to your favourites!</button>
  </div>
</template>

<script>
import { eventBus } from "../main.js"
import FavouriteProducts from './FavouriteProducts.vue'

export default {
  name: "product-detail",
  props: ["product", "favouriteProducts"],
  methods: {
  addToFavourites: function() {
      eventBus.$emit("favourite-product", this.product)
    },
    goToSite(product_link){
      window.location.href = product_link
    }
  }
}
</script>

<style lang="css" scoped>
#product-detail {
  border: 1px solid LightCoral;
  background-color: ghostwhite;
  opacity: 0.85;
  margin: 40px;
  padding: 10px;
}

h3 {
  text-align: center;
  font-weight: 900;
}

button {
  font-family: 'PT Sans', sans-serif;
  font-size: 15px;
}

button:hover {
  background-color: LightCoral;
}
</style>
