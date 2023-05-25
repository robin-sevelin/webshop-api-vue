<script setup lang="ts">
  import axios from 'axios';
  import { onMounted, ref } from 'vue';
  import { IProduct } from '../models/IProduct';
  import { IResponse } from '../models/IResponse';
  import AppProduct from './AppProduct.vue';

  onMounted(() => {
    getProducts();
  });
  const products = ref<IProduct[]>([]);

  const getProducts = async () => {
    let response = await axios.get<IResponse>(
      'https://medieinstitutet-wie-products.azurewebsites.net/api/products'
    );

    products.value = response.data;
  };
</script>

<template>
  <div class="products-container">
    <AppProduct :product="product" v-for="product in products" />
  </div>
</template>

<style scoped>
  .products-container {
    margin: auto;
    display: flex;
    flex-direction: row;
    max-width: 1600px;
    flex-wrap: wrap;
    gap: 2rem;
    padding-bottom: 150px;
    align-items: center;
    justify-content: center;
  }
</style>
