<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "app",
  components: {},
  data() {
    return {};
  },
  mounted() {
    // this.axios.get("/user/login").then(res => {
    //   this.res = res;
    // });
    this.getUser();
    this.getCartCount();
  },
  methods: {
    getUser() {
      this.axios.get("/user").then((res = {}) => {
        this.$store.dispatch("saveUserName", res.username);
      });
    },
    getCartCount() {
      this.axios.get("/carts/products/sum").then((res = 0) => {
        this.$store.dispatch("saveCartCount", res);
      });
    }
  }
};
</script>

<style lang="less">
#app {
  width: 1226px;
  min-width: 1226px;
  margin: 0 auto;
  box-sizing: border-box;
}
</style>
