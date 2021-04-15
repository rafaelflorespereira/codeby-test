<template>
<div>
  <h1>Carrinho de Compras</h1>
  <ul>
    <li v-for="product in shoppingCartDetails.items" :key="product.uniqueId">
      <product :product="product"/>
    </li>
  </ul>
  <section id="total">
    <p>Total</p>
    <p>{{shoppingCartDetails.value}}</p>
    <p>{{total}}</p>
  </section>
</div>
</template>

<script>
import Product from './Product'
export default {
  components: {
    Product
  },
  props: ['shoppingCartDetails'],
  computed: {
    total() {
      var total = 0;
      this.shoppingCartDetails.items.forEach(product => {
        total += product.sellingPrice
      });
      return total
    }
  }
}
</script>

<style>

</style>