<template>
  <h2>Catalog</h2>
  <div class="v-catalog">
    <router-link :to="{ name: 'cart' }">
      <div class="v-catalog__link_to_cart">Cart: {{ CART.length }}</div>
    </router-link>

    <div class="v-catalog__list">
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
    ...mapGetters(['PRODUCTS', 'CART']),
  },
  mounted() {
    this.GET_PRODUCT_FROM_API();
  },
};
</script>

<style lang="scss" scoped>
.v-catalog {
  &__list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    align-items: center;
  }
  &__link_to_cart {
    position: absolute;
    top: 10px;
    right: 10px;
    padding: $padding * 2;
    border: solid 2px #aeaeae;
  }
}
</style>
