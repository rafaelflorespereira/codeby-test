<template>
  <div>
    <img :src="product.imageUrl" alt="product-img" />
    <div>
      <h3>{{ product.name }}</h3>
      <p>{{ product.price }}</p>
      <p>{{ product.sellingPrice }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["product"],
};
</script>

<style>
</style>