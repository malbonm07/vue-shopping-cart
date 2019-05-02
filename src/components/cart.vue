<template lang="html">
  <div class="cart-item">
    <img :src="cartObject.fields.image.fields.file.url" alt="product">
    <div>
      <h4>{{cartObject.fields.title}}</h4>
      <h5>{{cartObject.fields.price | showPriceItem}}</h5>
      <span class="remove-item" @click="remove()">remove</span>
    </div>
    <div>
      <font-awesome-icon icon="chevron-up" @click="increaseOne()"></font-awesome-icon>
      <p class="item-amount">1</p>
      <font-awesome-icon icon="chevron-down" @click="reduceOne()"></font-awesome-icon>
    </div>
  </div>
</template>

<script>
export default {
  name: 'cart',
  data() {
    return {
      cartPrice: 0,
    }
  },
  props: {
    cartObject: {
      type: Object,
      required: true,
    },
    cartIndexObject: {
      type: Number,
      required: true,
    }
  },
  created() {
    //do something after creating vue instance
    this.cartPrice = this.cartObject.fields.price
    console.log(this.cartPrice)
  },
  methods: {
    remove() {
      this.$emit('deleteCartInBag', this.cartIndexObject)
      // console.log(this.cartIndexObject)
    },
    increaseOne() {
      this.cartObject.fields.price += this.cartPrice
    },
    reduceOne() {
      this.cartObject.fields.price -= this.cartPrice
      if(this.cartObject.fields.price <= 0) {
        this.$emit('deleteCartInBag', this.cartIndexObject)
      }
    }
  },
  filters: {
    showPriceItem(value) {
      return value = value.toFixed(2)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
