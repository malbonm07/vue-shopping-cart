<template>
  <div class="shopping-section">
    <!-- HEADER -->
      <header class="hero fadeIn">
        <div class="banner fadeIn">
          <h1 class="banner-title">Forniture collection</h1>
          <button class="banner-btn">shop now</button>
        </div>
      </header>
    <!-- HEADER -->

    <!-- PRODUCTS -->
      <section class="products">
        <div class="section-title">
          <h2>PRODUCTS</h2>
        </div>
        <div class="products-center">
          <article class="product" v-for="(p, index) in products" :key="index.key">
            <product :product="p" :i="index">
            </product>
          </article>
        </div>
      </section>
    <!-- PRODUCTS -->

    <!-- FOOTER -->
    <footer class="footer">
      <div class="footer-center">
        <section class="rights-reserved">
          <h5 class="rights-reserved__description "> COLLECTION, 2019. ALL RIGHTS RESERVED
          </h5>
        </section>
      </div>
    </footer>
    <!-- FOOTER -->
  </div>
</template>

<script>
import productsList from "../products.js"
import product from "./product.vue"

export default {
  name: 'HelloWorld',
  components: {
    product
  },
  data() {
    return {
      products: [],
    }
  },
  created() {
    //do something after creating vue instance
    this.products = productsList()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
  @import "../scss/styles";
</style>
