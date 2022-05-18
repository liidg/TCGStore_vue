<template>
  <div class="home">
    <section class="hero is-medium is-dark mb-6">
      <div class="hero-body has-text-centered">
        <p class="title mb-6">
          Bienvenido/a a TCG Store
        </p>
        <p class="subtitle">
          El mejor lugar para comprar tus cartas
        </p>
      </div>
    </section>

    <div class="columns is-multiline">
      <div class="column is-12">
        <h2 class="is-size-2 has-text-centered">Ultimos Productos</h2>
      </div>

      <div
      class="column is-3"
      v-for="product in latestProducts"
      v-bind:key="product.id"
      >
        <div class="box">
          <figure class="image mb-3">
            <img v-bind:src="product.get_image">
          </figure>

          <h3 class="is-size-4">{{ product.name }}</h3>
          <p class="is-size-6 has-text-grey">${{ product.price }}</p>


          <router-link v-bind:to="product.get_absolute_url" class="button is-dark mt-4">Ver Detalles</router-link>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import axios from 'axios'


export default {
  name: 'Home',
  data() {
    return {
      latestProducts: []
    }
  },
  components: {
  },
  mounted() {
    this.getLatestProducts()

    document.title ='TCGStore'
  },
  methods: {
    async getLatestProducts() {
      this.$store.commit('setIsLoading', true)

      await axios
        .get('/api/v1/latest-products/')
        .then(response => {
          this.latestProducts = response.data
        })
        .catch(error => {
          console.log(error)
        })

      this.$store.commit('setIsLoading', false)  
    }
  }
}
</script>

