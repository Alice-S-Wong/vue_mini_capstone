<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>{{product.name}}</h2>
    <p>Price: ${{product.price}}</p>
    <p>Description: {{product.description}}</p>
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
  methods: {}
};
</script>