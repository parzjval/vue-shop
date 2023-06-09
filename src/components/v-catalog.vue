<template>
  <h2>Catalog</h2>
  <div class="v-catalog">
    <vCatalogItem
      v-for="item in PRODUCTS"
      :key="item.article"
      :item="item"
    />
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
    ...mapActions(['GET_PRODUCT_FROM_API']),
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
