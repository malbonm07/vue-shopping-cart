<template>
  <div id="app">
    <nav id="nav" class="navbar">
      <div class="navbar-center">
        <span class="nav-icon">
          <router-link to="/" >Home</router-link> |
          <router-link to="/about">About</router-link>
        </span>
        <h2 class="navbar-center__title">LOGO<span>COMPANY</span> </h2>
        <div class="cart-btn" @click="showCart()">
          <span class="nav-icon">
            <font-awesome-icon icon="cart-plus"></font-awesome-icon>
          </span>
          <div class="cart-items">0</div>
        </div>
      </div>
    </nav>
    <router-view/>
    <!-- cart -->
      <div :class="['cart-overlay', {'transparentBcg' : showProp}]">
        <div :class="['cart', {'showCart' : showProp}]">
          <span class="close-cart" @click="closeCart()">
            <font-awesome-icon icon="times"></font-awesome-icon>
          </span>
          <h2>your cart</h2>
          <div class="cart-content">
            <!-- cart-item -->
            <div class="cart-item">
              <img src="https://images.pexels.com/photos/164595/pexels-photo-164595.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500" alt="product">
              <div>
                <h4>queen bed</h4>
                <h5>$9.00</h5>
                <span class="remove-item">remove</span>
              </div>
              <div>
                <i class="fas fa-chevron-up"></i>
                <p class="item-amount">1</p>
                <i class="fas fa-chevron-down"></i>
              </div>
            </div>
            <!-- end cart-item -->
            <div class="cart-footer">
              <h3>your total : $<span class="cart-total">0</span></h3>
              <button class="clear-cart banner-btn">clear cart</button>
            </div>
          </div>
        </div>
      </div>
    <!-- end cart -->
  </div>
</template>

<script type="text/javascript">
  export default {
    data() {
      return {
        showProp: true,
      }
    },
    methods: {
      showCart() {
        this.showProp = !this.showProp;
        console.log(this.showProp)
      },
      closeCart() {
        this.showProp = !this.showProp;
      }
    }
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
/*###########################     navbar    ############################################*/
.navbar {
  position: sticky;
  top: 0;
  height: 60px;
  width: 100%;
  display: flex;
  align-items: center;
  background: $tertiary-color;
  z-index: 1;
  box-shadow: 0 2px 4px rgba(154, 157, 120,.5);
}
.navbar-center {
  width: 100%;
  max-width: 1170px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 1.5rem;
  &__title {
    span {
      color: $secondary-color;
    }
  }
}
.nav-icon {
  font-size: 1.5rem;
}
.cart-btn {
  position: relative;
  cursor: pointer;
}
.cart-items {
  position: absolute;
  top: -12px;
  right: -8px;
  background: $secondary-color;
  padding: 0 5px;
  border-radius: 40%;
  color: $body-color;
}
/*###########################     end navbar    ############################################*/
</style>
