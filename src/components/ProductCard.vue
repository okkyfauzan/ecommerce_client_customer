<template>
  <div class="col-md-4">
    <div class="card mt-5">
      <img :src="product.image_url" class="card-img-top" style="height: 40vh;">
      <div class="card-body">
        <h5 class="card-title">{{ product.name }}</h5>
        <p class="card-text">{{ product.price | currency }}</p>
        <p class="card-text">Stock : {{ product.stock }}</p>
        <a href="#" class="btn btn-info d-grid mt-2"
        @click.prevent="addCart({ ProductId: product.id, price: product.price })">
        Add To Cart
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: ['product'],
  methods: {
    createCart () {
      const token = localStorage.getItem('access_token')
      if (!token) {
        this.$router.push({ name: 'Login' })
      }
    },
    addCart (payload) {
      const token = localStorage.getItem('access_token')
      if (!token) {
        this.$router.push({ name: 'Login' })
      } else {
        this.$store.dispatch('addCart', payload)
      }
    }
  }
}
</script>

<style>

</style>
