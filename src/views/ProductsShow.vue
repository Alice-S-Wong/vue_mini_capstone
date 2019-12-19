<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>{{product.name}}</h2>
    <p>Price: ${{product.price}}</p>
    <p>Description: {{product.description}}</p>
    <router-link v-bind:to="`/products/${product.id}/edit`">Edit Product</router-link>
    <br>
    <button v-on:click="destroyProduct(product)">Destroy Product</button>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Show Page",
      product: {}
    };
  },
  created: function() {
    axios.get(`api/products/${this.$route.params.id}`).then(response => {
      this.product = response.data;
    });
  },
  methods: {
    destroyProduct: function(product) {
      axios.delete(`api/products/${product.id}`).then(response => {
        this.$router.push("/products");
      });
    }
  }
};
</script>