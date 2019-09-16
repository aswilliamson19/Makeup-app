<template lang="html">
  <div id="favourites">
    <h3>Your Favourite Products...</h3>
    <ul v-for="product in favouriteProducts" :product="product" :key="product.id">
      <li :value="product">{{ product.name }}</li>
      <button v-on:click="displayInfo">More info?</button>
      <button :product="selectedProduct" v-on:click="removeFromFavourites">Remove From Favourites</button>
    </ul>
  </div>
</template>

<script>
import { eventBus } from "../main.js"

export default {
  name: "favourite-products",
  data() {
    return {
      "favouriteProduct": {},
      "selectedProduct": null
    }
  },
  props: ["favouriteProducts", "product"],
  methods: {
    removeFromFavourites: function(product) {
      const index = this.favouriteProducts.indexOf(product);
      this.favouriteProducts.splice(index, 1)
      eventBus.$emit("favouriteProducts", this.product)
    },
    displayInfo: function() {
      eventBus.$emit("product-selected", this.selectedProduct)
    }
  }
}
</script>

<style lang="css" scoped>
button {
  font-family: 'PT Sans', sans-serif;
  font-size: 15px;
  margin-right: 10px;
}

button:hover {
  background-color: LightCoral;
}
</style>
