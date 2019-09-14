<template lang="html">
  <div id="dropdown">
    <label for="product-selection">Select a product you would like to know more about...</label>
    <select v-on:change="handleSelect" v-model="selectedProduct">
      <!-- <option value=""></option> -->
      <option v-for="product in products" :value="product">{{product.name}}</option>
    </select>
  </div>
</template>

<script>
import { eventBus } from "../main.js"

export default {
  name: "product-list",
  data() {
    return {
      "selectedProduct": {}
    }
  },
  props: ["products"],
  methods: {
    handleSelect(){
      eventBus.$emit("product-selected", this.selectedProduct)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
