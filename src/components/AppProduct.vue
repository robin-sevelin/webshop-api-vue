<script setup lang="ts">
  import { IProductProps } from '../models/IProductProps';

  const props = defineProps<IProductProps>();
</script>

<template>
  <div class="product">
    <h3>{{ props.product.name }}</h3>
    <p>{{ props.product.description }}</p>
    <p>{{ props.product.year }}</p>
    <p>Price {{ props.product.price }} kr</p>
    <img
      :src="props.product.imageUrl"
      :alt="props.product.name"
      width="150"
      height="230"
    />
  </div>
</template>

<style scoped>
  .product {
    max-width: 300px;
    display: flex;
    flex-direction: column;
    padding: 2rem;
    justify-content: center;
    align-items: center;
  }
</style>
