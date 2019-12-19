<template>
  <div class="ProductsIndex">
    <h1>{{ message }}</h1>
    <div v-for="product in products">
      <h2>{{product.name}}</h2>
      <p>id: {{product.id}}</p>
      <p>Price: ${{product.price}}</p>
      <p>Description: {{product.description}}</p>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Products Index",
      products: []
    };
  },
  created: function() {
    axios.get("/api/products").then(response => {
      this.products = response.data;
    });
  },
  methods: {}
};
</script>