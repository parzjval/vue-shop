<template>
  <div class="v-cart">
    <h1>Cart</h1>
    <v-cart-item
      v-for="(item, index) in cart_data"
      :key="item.article"
      :cart_item_data="item"
      @deleteFromCart="deleteFromCart(index)"
    />
  </div>
</template>

<script>
import vCartItem from './v-cart-item.vue';
import { mapActions } from 'vuex';

export default {
  name: 'v-cart',
  components: {
    vCartItem,
  },
  props: {
    cart_data: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  methods: {
    ...mapActions(['DELETE_FROM_CART']),
    deleteFromCart(index) {
      this.DELETE_FROM_CART(index);
    },
  },
};
</script>

<style lang="scss" scoped>
//TODO варавнивание по центру и паддинги
.v-cart {
  display: flex;
  flex-direction: column;
  justify-content: center;
  // align-items: center;
  width: 90%;
}
</style>
