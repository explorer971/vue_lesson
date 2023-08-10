<template>
  <div class="v-name-wrapper">

    <keep-alive>
      <router-view></router-view>
    </keep-alive>

  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "v-name-wrapper",
  props: {},
  data() {
    return {
      title: "hello",
    };
  },
  computed: {
    ...mapGetters(["CART"]),
  },
  methods: {},
  watch: {},
  mounted() {
    console.log("hello im here");
  },
};
</script>

<style>
.v-name-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  max-width: 980px;
  margin: 0px auto;
}
</style>
