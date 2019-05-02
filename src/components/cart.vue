<template lang="html">
  <div class="cart-item">
    <img :src="cartObject.fields.image.fields.file.url" alt="product">
    <div>
      <h4>{{cartObject.fields.title}}</h4>
      <h5>{{cartObject.fields.price}}</h5>
      <span class="remove-item" @click="remove()">remove</span>
    </div>
    <div>
      <font-awesome-icon icon="chevron-up"></font-awesome-icon>
      <p class="item-amount">1</p>
      <font-awesome-icon icon="chevron-down"></font-awesome-icon>
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
  methods: {
    remove() {
      this.$emit('deleteCartInBag', this.cartIndexObject)
      // console.log(this.cartIndexObject)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
