<template lang="html">
  <div class="product-div">
      <div class="img-container">
        <img :src="product.fields.image.fields.file.url">
        <button class="bag-btn" @click="addToBag()">
          <i class="fas fa-shopping-cart"></i>
          add to bag
        </button>
      </div>
      <h3>{{product.fields.title}}</h3>
      <h4>{{product.fields.price | productsFixed}}</h4>
  </div>
</template>

<script>
export default {
  name: 'product',
  props: {
    product: {
      type: Object,
      required: true,
    },
    indexProduct: {
      type: Number,
      required: true,
    }
  },
  methods: {
    addToBag() {
      this.$emit("selected", this.indexProduct)
    }
  },
  filters: {
    productsFixed(value) {
      return value = value.toFixed(2);
    }
  }
}
</script>

<style lang="css" scoped>
.product-div {
  position: relative;

}
</style>
