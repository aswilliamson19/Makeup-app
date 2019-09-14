<template lang="html">
  <div v-if="product" id="product-detail">
    <h3>{{ product.name }}, made by {{ product.brand }}</h3>
    <p>{{ product. type }}</p>
    <p>{{ product.description }}</p>
    <!-- <label for="buy-button">You can buy {{ product.name }} here: </label> -->
    <!-- <button v-on:click="linkToSellersWebsite" name="button">Shop for product!</button> -->
  </div>
</template>

<script>
import { eventBus } from "../main.js"


export default {
  name: "product-detail",
  props: ["product"]
}
</script>

<style lang="css" scoped>
</style>
