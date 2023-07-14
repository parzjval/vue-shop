<template>
  <div>
    <vMainWrapper />
    <!-- <vCatalog />
  <vCart /> -->
  </div>
</template>

<script>
import vMainWrapper from './components/v-main-wrapper.vue';
// import vCatalog from './components/v-catalog.vue';
// import vCart from './components/v-cart.vue';

export default {
  name: 'App',
  components: {
    vMainWrapper,
    // vCatalog,
    // vCart,
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
