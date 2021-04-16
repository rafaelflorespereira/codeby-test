<template>
  <div class="product">
    <img :src="product.imageUrl" class="product__image" alt="product-img" />
    <div class="product__info">
      <h3 class="product__info-name">{{ product.name | sUcfirst }}</h3>
      <p class="product__info-price">
        R&#36;{{ (product.price * product.quantity) | decimalPrice }}
      </p>
      <p class="product__info-selling-price">
        R&#36;{{ (product.sellingPrice * product.quantity) | decimalPrice }}
      </p>
    </div>

    <div class="product__subtotal">
      <span class="product__subtotal--icon" @click="removeItem">&#8722;</span>
      <span class="product__subtotal--quantity">{{ product.quantity }}</span>
      <span class="product__subtotal--icon" @click="addItem">&#43;</span>
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
    /* Capitalizing first string.
    code got from https://dzone.com/articles/capitalize-first-letter-string-javascript
    added last to lower the rest of the string.
    */
    sUcfirst(string) {
      return string.charAt(0).toUpperCase() + string.slice(1).toLowerCase();
    },
  },
  methods: {
    addItem() {
      this.product.quantity++;
    },
    removeItem() {
      if (this.product.quantity > 0) {
        this.product.quantity--;
      }
    },
  },
};
</script>

<style lang="scss">
.product {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
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
    flex-grow: 3;
    flex-direction: column;
    align-items: flex-start;
    &-name {
      font-size: 1.5rem;
      font-weight: 900;
    }
    &-price {
      color: #999;
      margin: 0.4rem 0;
      font-weight: 600;
      font-size: 1.1rem;
    }
    &-selling-price {
      font-weight: 600;
      color: black;
      font-size: 1.5rem;
    }
  }
  &__subtotal {
    font-size: 1.5rem;
    align-self: center;
    &--icon {
      margin: .5rem;
      cursor: pointer;
    }
    &--quantity {
      font-weight: 600;
    }
  }
}
</style>