<template>
  <div class="v-catalog-item">
    <img
      :src="require('../../assets/images/' + product.image)"
      alt="Product picture"
      class="img"
    />
    <p>
      <strong> {{ product.name }} </strong>
    </p>
    <p>{{ product.price }} р.</p>
    <button
      class="btn"
      @click="addToCart"
    >
      Add to cart
    </button>
  </div>
</template>

<script>
export default {
  name: 'v-catalog-item',
  props: {
    product_data: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  data() {
    return {
      product: this.product_data,
    };
  },
  methods: {
    addToCart() {
      this.$emit('addToCart', this.product);
    },
  },
  mounted() {
    this.product['quantity'] = 1;
  },
};
</script>

<style scoped lang="scss">
.v-catalog-item {
  flex-basis: 25%;
  box-shadow: 0 0 8px 0 #e0e0e0;
  padding: $padding * 2;
  margin-bottom: $margin * 2;
}

.img {
  width: 100%;
}
</style>
