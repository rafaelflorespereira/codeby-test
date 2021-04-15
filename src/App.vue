<template>
  <div id="app">
    <button @click="getAboveItems">Show items above price</button>
    <button @click="getBelowItems">Show items below price</button>
    <shopping-cart v-show="open" @close="close" :shoppingCartDetails="items"/>
  </div>
</template>

<script>
import ShoppingCart from './components/ShoppingCart.vue'
import aboveItems from './data/priceAbove.json'
import belowItems from './data/priceBelow.json'

export default {
  name: 'App',
  components: {
    ShoppingCart
  },
  data() {
    return {
      items: [],
      open: false
    }
  },
  methods:{
    getAboveItems() {
      this.open = true
      this.items = aboveItems
    },
    getBelowItems() {
      this.open = true
      this.items = belowItems
    },
    close(value) {
      this.open = value
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
