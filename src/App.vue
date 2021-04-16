<template>
  <div id="app">
    <div class="welcome">
      <h3>Welcome!</h3>
      <p>
        The above or below selection will get the different json file given in
        the test.
      </p>
    </div>
    <button class="blue-button" @click="getAboveItems">
      Show items above price
    </button>
    <button class="blue-button" @click="getBelowItems">
      Show items below price
    </button>
    <transition name="fade">
      <div v-show="open" class="pop-up">
        <shopping-cart
          v-show="open"
          @close="close"
          :shoppingCartDetails="items"
        />
      </div>
    </transition>
  </div>
</template>

<script>
import ShoppingCart from "./components/ShoppingCart.vue";
import aboveItems from "./data/priceAbove.json";
import belowItems from "./data/priceBelow.json";

export default {
  name: "App",
  components: {
    ShoppingCart,
  },
  data() {
    return {
      items: [],
      open: false,
    };
  },
  methods: {
    getAboveItems() {
      this.open = true;
      this.items = aboveItems;
    },
    getBelowItems() {
      this.open = true;
      this.items = belowItems;
    },
    close(value) {
      this.open = value;
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
html {
  box-sizing: border-box;
}

@font-face {
  font-family: "Poppins";
  src: url("assets/fonts/Poppins-Regular.ttf") format("truetype");
  font-weight: normal;
}

@font-face {
  font-family: "Poppins";
  src: url("assets/fonts/Poppins-SemiBold.ttf") format("truetype");
  font-weight: 600;
}

@font-face {
  font-family: "Poppins";
  src: url("assets/fonts/Poppins-Bold.ttf") format("truetype");
  font-weight: bold;
}

@font-face {
  font-family: "Poppins";
  src: url("assets/fonts/Poppins-Black.ttf") format("truetype");
  font-weight: 900;
}

#app {
  text-align: center;
  font-family: Poppins;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  margin: 0 20%;
}

.welcome {
  padding: 0 4rem;
  color: rgb(33, 122, 1);
  background-color: rgb(199, 255, 166);
  border-radius: 10px;
  font-size: 2rem;
}

.pop-up {
  height: auto;
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
  background-color: rgb(209, 216, 229);
  z-index: 9999;
  -webkit-backdrop-filter: blur(10px);
  backdrop-filter: blur(10px);
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s 0.2s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
