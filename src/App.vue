<template>
  <div id="app">
    <nav id="nav" class="navbar">
      <div class="navbar-center">
        <span class="nav-icon">
          <router-link to="/" >Home</router-link> |
          <router-link to="/about">About</router-link>
        </span>
        <h2 class="navbar-center__title">LOGO<span>COMPANY</span> </h2>
      </div>
    </nav>
    <router-view/>
  </div>
</template>

<script type="text/javascript">
// import cart from "./components/cart"
  export default {
    // components: {
    //   cart
    // },
    data() {
      return {
        // showProp: true,
        // carts: []
      }
    },
    // methods: {
    //   showCart() {
    //     this.showProp = !this.showProp;
    //     console.log(this.showProp)
    //     this.carts = JSON.parse(localStorage.getItem('products') || "[]");
    //     console.log(this.carts)
    //   },
    //   closeCart() {
    //     this.showProp = !this.showProp;
    //   }
      // deleteCart() {
      //   this.$bus.$on("deleteCartInBag", i => {
      //     console.log(this.carts[i])
      //   })
        // this.carts.splice(i, 1);
        // console.log(i)
        // localStorage.setItem("products", JSON.stringify(this.carts));
      // }
    // },
    // create() {
    // }
  }
</script>

<style lang="scss">

@import "scss/styles";

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
