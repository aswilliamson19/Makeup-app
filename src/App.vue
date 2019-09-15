<template lang="html">
  <div id="page">
      <h1>Find your perfect makeup...</h1>
      <div id="product-list">
      <product-list :products="products" />
    </div>
    <div id="product-detail">
      <product-detail :product="selectedProduct" :favouriteProducts="favouriteProducts" />
    </div>
    <div id="favourite-list">
      <favourite-products :favouriteProducts="favouriteProducts" />
    </div>
  </div>
</template>

<script>
import { eventBus } from "./main.js";
import ProductList from "./components/ProductList.vue"
import ProductDetail from "./components/ProductDetail.vue"
import FavouriteProducts from "./components/FavouriteProducts.vue"

export default {

data() {
  return {
    products: [],
    selectedProduct: null,
    favouriteProducts: []
  }
},

components: {
  "product-list": ProductList,
  "product-detail": ProductDetail,
  "favourite-products": FavouriteProducts
},

  mounted() {
    fetch('http://makeup-api.herokuapp.com/api/v1/products.json')
    .then(result => result.json())
    .then(products => this.products = products)
    eventBus.$on("product-selected", (product) => {
      this.selectedProduct = product;
    })
    eventBus.$on("favourite-product", (product) => {
      this.favouriteProducts.push(product);
    })
  }
}
</script>

<style lang="css" scoped>
#page {
  font-family: 'PT Sans', sans-serif;
  font-size: 25px;
  font-weight: 500;
}

#product-list, #product-detail, #favourite-list {
  font-size: 25px;
}

</style>
