<template>
  <h2>Catalog</h2>
  <div class="v-catalog">
    <vCatalogItem
      v-for="item in items_data"
      :key="item.article"
      :item="item"
    />
  </div>
</template>

<script>
import vCatalogItem from './v-catalog-item.vue';

export default {
  name: 'v-catalog',
  components: {
    vCatalogItem,
  },
  props: {
    items_data: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style scoped>
.v-catalog {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
}
</style>
