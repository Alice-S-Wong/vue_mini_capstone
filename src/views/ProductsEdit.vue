<template>
  <div class="EditProduct">
    <h1>{{ message }}</h1>
    <p>Name:<input v-model="product.name"></p>
    <p>Price:<input v-model="product.price"></p>
    <p>Description:<input v-model="product.description"></p>
    <button v-on:click="editProduct(product)">Edit Product</button>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Edit a Product",
      product: {}
    };
  },
  created: function() {
    axios.get(`/api/products/${this.$route.params.id}`).then(response => {
      this.product = response.data;
    });
  },
  methods: {
    editProduct: function(product) {
      var params = {
        name: product.name,
        price: product.price,
        description: product.description
      };
      axios.patch(`/api/products/${product.id}`, params).then(response => {
        this.$router.push(`/products/${product.id}`);
      });
    }
  }
};
</script>