<template>
  <div class="product">
    <img :src="product.imageUrl" class="product__image" alt="product-img" />
    <div class="product__info">
      <h3 class="product__info-name">{{ product.name }}</h3>
      <p class="product__info-price">{{ product.price }}</p>
      <p class="product__info-selling-price">{{ product.sellingPrice }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["product"],
};
</script>

<style lang="scss">
.product {
  display: flex;
  flex-direction: row;
  height: 20rem;
  &__image {
    width: 25%;
    border: 1px solid #999;
    object-fit: cover;
  }
  &__info {
    &-name {
    }
    &-price {
    }
    &-selling-price {
    }
  }
}
</style>