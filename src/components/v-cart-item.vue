<template>
  <div class="v-cart-item">
    <div class="v-cart-item__content">
      <img 
        :src="require('../assets/images/' + cart_item_data.image)" 
        :alt="cart_item_data.name" 
        class="v-cart-item__image"
      >
      <div class="v-catalog-item__name">
        {{ cart_item_data.name }}
      </div>
      <div class="v-catalog-item__price">
        Цена: <span>{{ cart_item_data.price }}</span> $
      </div>
      <div class="v-catalog-item__about">
        {{ cart_item_data.article }}
      </div>
      <div class="v-catalog-item__about">
        {{ cart_item_data.about }}
      </div>
      <div class="v-catalog-item__about">
        Quantity {{ cart_item_data.quantity }}
      </div>
    </div>
    <button @click="deleteFromCart" class="v-catalog-item__btn">Delete</button>
  </div>
</template>

<script>

export default {
  name: "v-cart-item",
  props: {
    cart_item_data: {
      type: Object,
      defoult() {
        return {};
      }
    }
  },
  data() {
    return {};
  },
  computed: {},
  methods: {
    deleteFromCart() {
      this.$emit("deleteFromCart")
    }
  },
  watch: {},
  mounted() {},
};
</script>
