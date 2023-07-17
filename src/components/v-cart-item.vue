<template>
  <div class="v-cart-item">
    <img
      :src="require('../assets/images/' + cart_item_data.image)"
      alt="Product picture"
      class="img"
    />
    <div class="v-cart-item__info">
      <p>{{ cart_item.name }}</p>
      <p>{{ cart_item.price }} p.</p>
      <p>{{ cart_item.article }}</p>
    </div>
    <div class="v-cart-item__quantity">
      <p>Qty:</p>
      <span>
        <span @click="decrementItem">–</span>
        {{ cart_item.quantity }}
        <span @click="incrementItem">+</span>
      </span>
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
    decrementItem() {
      this.$emit('decrement');
    },

    incrementItem() {
      this.$emit('increment');
    },

    deleteFromCart() {
      this.$emit('deleteFromCart');
    },
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
