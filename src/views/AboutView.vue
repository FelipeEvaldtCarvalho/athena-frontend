<template>
  <div>
    <h1>about</h1>
    <div v-for="product in products" :key="product.id">
      <h4>{{ product.name }}</h4>
      <h4>{{ product.price }}</h4>
      <h4>{{ product.category_id }}</h4>
      <h4>{{ product.description }}</h4>
      <hr>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'AboutComponent',
  data () {
    return{
      products: {}
    }
  },
  mounted() {
    this.getProducts();
  },
  methods: {
    getProducts(){
        axios.get('http://localhost/api/products')
        .then(response => {this.products = response.data.data ;})
        .catch(error => console.log(error));
    },
  },

}
</script>

<style>

</style>