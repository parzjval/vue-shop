<template>
  <div class="v-catalog-item">
    <img
      :src="require('../assets/images/' + item.image)"
      alt="Product picture"
      class="img"
    />
    <p>
      <strong> {{ item.name }} </strong>
    </p>
    <p>{{ item.price }} р.</p>
    <button class="btn">Add to cart</button>
  </div>
</template>

<script>
export default {
  name: 'v-catalog-item',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped lang="scss">
.v-catalog-item {
  margin-bottom: $margin * 2;
  background: lightgrey;
  max-width: 20%;
  max-height: 20%;
}

.img {
  width: 100%;
  height: 100%;
}
</style>
