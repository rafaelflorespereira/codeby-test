<template>
  <div class="shopping-cart">
    <div class="shopping-cart__header u-bottom-border">
      <h1 class="shopping-cart__header--title">Meu carrinho</h1>
      <button
        class="shopping-cart__header--close-button"
        @click="$emit('close', false)"
      >
        &times;
      </button>
    </div>
    <ul class="list u-bottom-border">
      <li
        class="item"
        v-for="product in shoppingCartDetails.items"
        :key="product.uniqueId"
      >
        <product :product="product" />
      </li>
    </ul>
    <section class="total u-bottom-border">
      <p class="total__text">Total</p>
      <p class="total__price">R&#36;{{ shoppingCartDetails.value | decimalPrice }}</p>
      <p v-show="total > 1000" class="total__notification">
        Parabéns, sua compra tem frete grátis !
      </p>
    </section>
    <div class="button-placeholder">
      <button class="blue-button">Finalizar compra</button>
    </div>
  </div>
</template>

<script>
import Product from "./Product";
export default {
  components: {
    Product,
  },
  props: ["shoppingCartDetails"],
  computed: {
    total() {
      var total = 0;
      this.shoppingCartDetails.items.forEach((product) => {
        total += product.sellingPrice;
      });
      return total;
    },
  },
  filters: {
    decimalPrice(price) {
      return (price/100).toFixed(2)
    }
  }
};
</script>

<style lang="scss">
.shopping-cart {
  width: 50vw;
  margin: 5rem auto;
  background-color: white;
  border-radius: 20px;
  box-shadow: 1rem 1rem 2rem rgba(0, 0, 0, 0.2), -1rem 1rem 2rem rgba(0, 0, 0, 0.2);
  &__header {
    padding: 2rem;
    position: relative;
    padding-bottom: 2rem;
    &--title {
      font-weight: bold;
      font-size: 3rem;
    }
    &--close-button {
      border: none;
      position: absolute;
      top: 1rem;
      right: 1rem;
      font-size: 2rem;
      cursor: pointer;
    }
  }
}

.u-bottom-border {
  content: ""; /* This is necessary for the pseudo element to work. */
  display: block; /* This will put the pseudo element on its own line. */
  margin: 0 auto;
   /* This will center the border. */
  width: 100%;
  border-bottom: 2px solid #ccc;
}
.list {
  padding: 2rem;
}
.item {
  list-style: none;
}

.total {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  padding: 2rem;
  font-size: 3rem;
  color: black;
  font-weight: bolder;
  &__notification {
    width: 100%;
    color: rgb(33, 122, 1);
    background-color: rgb(199, 255, 166);
    border-radius: 100px;
    font-size: 2rem;
    margin: 5% 10% 0;
    padding: 0.8rem 0.3rem;
  }
}
.button-placeholder{
  padding: 2rem;
}
.blue-button {
  color: white;
  background-color: rgb(59, 116, 242);
  border: 2px solid rgb(59, 116, 242);
  cursor: pointer;
  border-style: none;
  border-radius: 10px;
  margin: 0 auto;
  width: 100%;
  font-size: 3rem;
  font-weight: bolder;
  padding: 1.5rem 0;
  transition: all .3s;
  &:hover {
    color:rgb(59, 116, 242);
    background-color: white;
    border: 2px solid rgb(59, 116, 242);
  }
}
</style>
