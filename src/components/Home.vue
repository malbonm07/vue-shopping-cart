<template>
  <div class="shopping-section">

    <div class="cart-btn" @click="showCart()">
      <span class="nav-icon">
        <font-awesome-icon class="cart-icon" icon="cart-plus"></font-awesome-icon>
      </span>
      <div class="cart-items">{{cartItems}}</div>
    </div>

    <!-- HEADER -->
      <header class="hero">
        <div class="banner">
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
          <article class="product" v-for="(p, index) in productsList" :key="index.key">
            <product
            :product="p"
            :indexProduct="index"
            @selected="productIndex">
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
    <!-- cart -->
      <div :class="['cart-overlay', {'transparentBcg' : showProp}]">
        <div :class="['cart', {'showCart' : showProp}]">
          <span class="close-cart" @click="closeCart()">
            <font-awesome-icon icon="times"></font-awesome-icon>
          </span>
          <h2>your cart</h2>
          <div class="cart-content">
            <!-- cart-item -->
            <div class="cart-product" v-for="(cart, indexCart) in productsBag.products" :key="indexCart.key">
              <cart
              :cartObject="cart"
              :cartIndexObject="indexCart"
              @deleteCartInBag="deleteCart"> </cart>
            </div>
            <!-- end cart-item -->
            <div class="cart-footer">
              <h3>your total : $<span class="cart-total">{{totalCart}}</span></h3>
              <button class="clear-cart banner-btn" @click="clearAll()">clear cart</button>
            </div>
          </div>
        </div>
      </div>
    <!-- end cart -->
  </div>
</template>

<script>
import productsList from "../products.js"
import product from "./product.vue"
import cart from "./cart"

export default {
  name: 'HelloWorld',
  components: {
    product,
    cart
  },
  data() {
    return {
      productsList: [],
      // products: [],
      productsBag: {
        products: [],
        productsToBuy: [],
        productsTotal: 0,
      },
      productsId: [],
      showProp: true,
    }
  },
  created() {
    //do something after creating vue instance
    this.productsList = productsList();
    // this.products = [...this.productsList]
    this.productsBag.products = JSON.parse(localStorage.getItem('products' || '[]'));
  },
  methods: {
    productIndex(index) {
      this.products = JSON.parse(localStorage.getItem('products' || '[]'));
      if(this.productsBag.products.length === 0) {
        this.productsBag.products.push(this.productsList[index])
        this.productsId.push(this.productsList[index].sys.id)
        localStorage.setItem("products", JSON.stringify(this.productsBag.products));
      }else if(this.productsId.indexOf(this.productsList[index].sys.id) < 0) {
        this.productsBag.products.push(this.productsList[index])
        this.productsId.push(this.productsList[index].sys.id)
        localStorage.setItem("products", JSON.stringify(this.productsBag.products));
        // console.log(this.productsBag.productsBagList)
        // console.log(this.products[index])
      }
    },
    showCart() {
      this.showProp = !this.showProp;
      this.productsBag.products = JSON.parse(localStorage.getItem('products'))
    },
    closeCart() {
      this.showProp = !this.showProp;
    },
    deleteCart(index) {
      // console.log(this.productsId)
      // console.log(this.productsId.indexOf(this.productsBag.products[index].sys.id))
      if(this.productsId.indexOf(this.productsBag.products[index].sys.id) >= 0) {
        this.productsId.splice(this.productsId.indexOf(this.productsBag.products[index].sys.id), 1)
        this.productsBag.products.splice(index, 1)
        localStorage.setItem("products", JSON.stringify(this.productsBag.products));
      }
      // console.log(this.productsId)
      // this.productsBag.productsToBuy.splice(index, 1);
      // console.log(this.productsId.indexOf(this.productsBag.productsBagList[index].sys.id))
      localStorage.setItem("products", JSON.stringify(this.productsBag.products));
    },
    clearAll() {
      if(this.productsBag.products.length >= 0) {
        this.productsBag.products.splice(0)
        this.productsId.splice(0)
        localStorage.setItem("products", JSON.stringify(this.productsBag.products));
      }
      localStorage.setItem("products", JSON.stringify(this.productsBag.products));
    }
  },
  computed: {
    cartItems() {
      return this.productsBag.products.length;
    },
    totalCart() {
      let totalBag = this.productsBag.products;
      let total = [];
      totalBag.forEach(cartItem => {
        total.push(cartItem.fields.price)
      })
      this.productsBag.productsTotal = total.reduce((acc, current) => {
        return acc + current
      }, 0)
      return this.productsBag.productsTotal.toFixed(2)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
  @import "../scss/styles";
</style>
