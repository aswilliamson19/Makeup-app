<template lang="html">
  <div>
    <h1>Find your perfect makeup...</h1>
    <product-list :products="products" />
    <product-detail :product="selectedProduct" />
  </div>
</template>

<script>
import { eventBus } from "./main.js";
import ProductList from "./components/ProductList.vue"
import ProductDetail from "./components/ProductDetail.vue"

export default {

data() {
  return {
    products: [],
    selectedProduct: null
  }
},

components: {
  "product-list": ProductList,
  "product-detail": ProductDetail
},

  mounted() {
    fetch('http://makeup-api.herokuapp.com/api/v1/products.json')
    .then(result => result.json())
    .then(products => this.products = products)
    eventBus.$on("product-selected", (product) => {
      this.selectedProduct = product;
    })
  }

}
</script>

<style lang="css" scoped>
</style>
