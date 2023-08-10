<template>
  <div class="v-cart">
    <div class="v-cart__header">
      <h1>Корзина</h1>
      <div class="v-catalog__link_to_cart">
        <span>Корзина: {{ CART.length }}</span>
        <router-link :to="{ name: 'catalog' }">
          <button class="v-catalog-item__btn">Вернуться в каталог</button>
        </router-link>
      </div>
    </div>
    

    <div v-if="!CART.length">Корзина пуста</div>

    <div class="v-cart-item__list">
      <vCartItem
        v-for="(item, index) in CART"
        :key="item.article"
        :cart_item_data="item"
        @deleteFromCart="deleteFromCart(index)"
      ></vCartItem>
    </div>
  </div>
</template>
  
<script>
import vCartItem from "./v-cart-item.vue";
import { mapActions, mapGetters } from "vuex";
export default {
  name: "v-cart",
  components: {
    vCartItem,
  },
  props: {
    cart_data: {
      type: Array,
      default() {
        return {};
      }
    }
  },
  data() {
    return {};
  },
  computed: {
    ...mapGetters(["CART"]),
  },
  methods: {
    ...mapActions(['DELETE_FROM_CART']),
    deleteFromCart(index) {
      this.DELETE_FROM_CART(index);
    },
  }
};
</script>
  
  <style>
</style>