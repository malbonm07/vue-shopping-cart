<template lang="html">
  <div>
      <div class="img-container">
        <img :src="product.fields.image.fields.file.url">
        <button class="bag-btn">
          <i class="fas fa-shopping-cart"></i>
          add to bag
        </button>
      </div>
      <h3>{{product.fields.title}}</h3>
      <h4>{{product.fields.price}}</h4>
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
    i: {
      type: Number,
      required: true,
    }
  }
}
</script>

<style lang="css" scoped>
</style>
