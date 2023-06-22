<template>
  <div>
    <h2>Catalog</h2>
    <div class="v-catalog">
      <vCatalogItem
        v-for="item in PRODUCTS"
        :key="item.article"
        :product_data="item"
        @addToCart="addToCart"
      />
    </div>
  </div>
</template>

<script>
import vCatalogItem from './v-catalog-item.vue';
import { mapActions, mapGetters } from 'vuex';

export default {
  name: 'v-catalog',
  components: {
    vCatalogItem,
  },
  methods: {
    ...mapActions(['GET_PRODUCT_FROM_API', 'ADD_TO_CART']),
    addToCart(data) {
      this.ADD_TO_CART(data);
    },
  },
  computed: {
    ...mapGetters(['PRODUCTS']),
  },
  mounted() {
    this.GET_PRODUCT_FROM_API();
  },
};
</script>

<style scoped>
.v-catalog {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  align-items: center;
}
</style>
