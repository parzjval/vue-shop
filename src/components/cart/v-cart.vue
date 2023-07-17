<template>
  <div class="v-cart">
    <h1>Cart</h1>
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
        @increment="increment(index)"
        @decrement="decrement(index)"
      />
    </p>

    <div class="v-cart__total">
      <p class="v-cart__total__name">Total:</p>
      <p>{{ cartTotalCost }} р.</p>
    </div>
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
    cartTotalCost() {
      let result = [];

      if (this.CART.length) {
        for (let item of this.CART) {
          result.push(item.price * item.quantity);
        }

        result = result.reduce((sum, el) => sum + el, 0);

        return result;
      } else {
        return 0;
      }
    },
    ...mapGetters(['CART']),
  },
  methods: {
    ...mapActions(['DELETE_FROM_CART', 'INCREMENT_CART_ITEM', 'DECREMENT_CART_ITEM']),
    increment(index) {
      this.INCREMENT_CART_ITEM(index);
    },
    decrement(index) {
      this.DECREMENT_CART_ITEM(index);
    },
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
  align-items: center;
  margin-bottom: 55;

  &__link_to_catalog {
    position: absolute;
    top: 10px;
    right: 10px;
    border: solid 2px #aeaeae;
    padding: $padding * 2;
  }

  &__total {
    position: fixed;
    bottom: 0px;
    right: 0px;
    left: 0px;
    background-color: green;
    color: white;
    display: flex;
    justify-content: center;
  }

  &__total__name {
    margin-right: $margin;
  }
}
</style>
