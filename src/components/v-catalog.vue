<template>
  <div class="v-catalog">
    <div class="v-catalog__header">
      <h1>Каталог</h1>

      <router-link :to="{ name: 'cart', params:{cart_data: CART} }" class="v-catalog__link_to_cart">
        Корзина: {{ CART.length }}
      </router-link>
    </div>
    
  
    <div class="v-catalog__list">
      <vCatalogItem
        v-for="product in PRODUCTS"
        :key="product.article"
        :product_data="product"
        @addToCart="addToCart"
      ></vCatalogItem>
    </div>
  </div>
</template>
  
  <script>
import vCatalogItem from "./v-catalog-item.vue";
import { mapActions, mapGetters } from "vuex";

export default {
  name: "v-catalog",
  components: { 
    vCatalogItem,
  },
  props: {},
  data() {
    return {};
  },
  computed:{
    ...mapGetters(["PRODUCTS", "CART"])
  },
  methods: {
    ...mapActions(["GET_PRODUCTS_FROM_API", "ADD_TO_CART"]),

    addToCart(data) {
      this.ADD_TO_CART(data);
    },
  },
  mounted(){
    this.GET_PRODUCTS_FROM_API().then((response)=> {
      if(response.data) {
        console.log("Данные пришли");
      }
    })
  }
};
</script>