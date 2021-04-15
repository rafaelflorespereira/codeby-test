<template>
  <div class="product">
    <img :src="product.imageUrl" class="product__image" alt="product-img" />
    <div>
      <h3 class="product__name">{{ product.name }}</h3>
      <p class="product__price">{{ product.price }}</p>
      <p class="product__selling-price">{{ product.sellingPrice }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["product"],
};
</script>

<style lang="scss">
</style>