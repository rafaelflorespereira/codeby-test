<template>
  <div class="product">
    <img :src="product.imageUrl" class="product__image" alt="product-img" />
    <div class="product__info">
      <h3 class="product__info-name">{{ product.name }}</h3>
      <p class="product__info-price">R&#36;{{ product.price | decimalPrice }}</p>
      <p class="product__info-selling-price">
        R&#36;{{ product.sellingPrice | decimalPrice }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["product"],
  filters: {
    decimalPrice(price) {
      return (price / 100).toFixed(2);
    },
  },
};
</script>

<style lang="scss">
.product {
  display: flex;
  flex-direction: row;
  height: 10rem;
  margin: 2rem auto;
  &__image {
    width: 10rem;
    border: 2px solid #ccc;
    object-fit: cover;
  }
  &__info {
    padding: 2rem;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    &-name {
      font-size: 1.5rem;
      font-weight: 800;
    }
    &-price {
      color: #999;
      margin: .4rem 0;
    }
    &-selling-price {
      font-weight: 600;
      color: black;
      font-size: 1.5rem;
    }
  }
}
</style>