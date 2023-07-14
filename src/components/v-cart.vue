<template>
  <h1>Cart</h1>
  <div class="v-cart">
    <p v-if="!CART.length">There is a no more product's in cart</p>
    <p>
      <router-link :to="{ name: 'catalog' }">
        <div class="v-cart__link_to_catalog">Back to catalog</div>
      </router-link>
      <v-cart-item
        v-for="(item, index) in CART"
        :key="item.article"
        :cart_item_data="item"
        @deleteFromCart="deleteFromCart(index)"
      />
    </p>
  </div>
</template>

<script>
import vCartItem from './v-cart-item.vue';
import { mapActions, mapGetters } from 'vuex';

export default {
  name: 'v-cart',
  components: {
    vCartItem,
  },
  computed: {
    ...mapGetters(['CART']),
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
.v-cart {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 90%;
}
</style>
