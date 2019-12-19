<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p>Name:<input v-model="newName"></p>
    <p>Price:<input v-model="newPrice"></p>
    <p>Description:<input v-model="newDescription"></p>
    <button v-on:click="createProduct()">Create Product</button>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Create a Product"
    };
  },
  created: function() {},
  methods: {
    createProduct: function() {
      var params = {
        name: this.newName,
        price: this.newPrice,
        description: this.newDescription
      };
      axios.post("/api/products", params).then(response => {
        this.$router.push("/products");
      });
    }
  }
};
</script>