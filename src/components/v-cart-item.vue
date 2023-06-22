<template>
  <div class="v-cart-item">
    <img
      :src="require('../assets/images/' + cart_item_data.image)"
      alt="Product picture"
      class="img"
    />
    <div class="v-cart-item__info">
      <p>{{ cart_item.name }}</p>
      <p>{{ cart_item.price }}</p>
      <p>{{ cart_item.article }}</p>
    </div>
    <div class="v-cart-item__quantity">
      <p>Qty:</p>
      {{ cart_item.quantity }}
    </div>
    <button @click="deleteFromCart">Delete</button>
  </div>
</template>

<script>
export default {
  name: 'v-cart-item',
  props: {
    cart_item_data: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  data() {
    return {
      cart_item: this.cart_item_data,
    };
  },
  methods: {
    deleteFromCart() {
      this.$emit('deleteFromCart');
    },
  },
  mounted() {
    // this.$set(this.cart_item_data, 'quantity', 1);
    this.cart_item['quantity'] = 1;
    // Vue.set(this.cart_item_data, 'quantity', 1);
  },
};
</script>

<style lang="scss" scoped>
.v-cart-item {
  display: flex;
  flex-wrap: nowrap;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 0 8px 0 #e0e0e0;
  margin-bottom: $margin * 2;
  padding: $padding * 2;
}

.img {
  max-width: 20%;
}
</style>
