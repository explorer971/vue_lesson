<template>
  <div class="v-catalog-item">
    <div class="v-catalog-item__content">
      <img 
        :src="require('../assets/images/' + product_data.image)" 
        :alt="product_data.name" 
        class="v-catalog-item__image"
      >
      <div class="v-catalog-item__name">{{ product_data.name }}</div>
      <div class="v-catalog-item__price">Цена: <span>{{ product_data.price }}</span> $</div>
      <div class="v-catalog-item__about">{{ product_data.about }}</div>
    </div>
    <button class="v-catalog-item__btn" @click="addToCart">add to cart</button>
  </div>
</template>

<script>
export default {
  name: "v-catalog-item",
  props: {
    product_data: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  data() {
    return {};
  },
  methods: {
    addToCart() {
        this.$emit("addToCart", this.product_data);
    },
  }
};
</script>