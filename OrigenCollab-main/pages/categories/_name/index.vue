<template lang="pug">
  v-app
    div(justify="center" align="center")
      h2.text-h2.categoryLink {{ this.$route.params.name }}
    v-row(justify="center" align="center")
      Product(v-for="product in products" v-bind:key="product._id" v-bind:product="product")
</template>

<script>
import Product from '~/components/Product/index.vue'

export default {
  data () {
    return {
      products: Object
    }
  },
  components: {
    Product
  },
  async fetch() {
    await this.$axios.$get('/product?category='+this.$route.params.name).then( (res) => this.products = res.product);
  }
}
</script>
