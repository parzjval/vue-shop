<template>
  <h1>Hello World!</h1>
  <vMainWrapper />
  <vCatalog :items_data="items_data" />
  <vCart />
</template>

<script>
import vMainWrapper from './components/v-main-wrapper.vue';
import vCatalog from './components/v-catalog.vue';
import vCart from './components/v-cart.vue';
import Data from '../db.json';

export default {
  name: 'App',
  components: {
    vMainWrapper,
    vCatalog,
    vCart,
  },
  data() {
    return {
      items_data: Data,
    };
  },
};
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
