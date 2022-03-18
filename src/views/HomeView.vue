<template>
  <div class="home">
      <Navbar />
      <div class="container">
        <Hero />
        <div class="row mt-3">
          <div class="col">
            <h2>Best <strong>Foods</strong></h2>
          </div>
          <div class="col">
            <router-link to="/foods" class="btn btn-warning float-right">Lihat Semua</router-link>
          </div>
        </div>
        <div class="row mb-3">
          <div class="col-md-4 mt-2" v-for="products in product" :key="products.id">
              <CardProduct :products="products"/>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from '@/components/Navbar.vue'
import Hero from '@/components/Hero.vue'
import CardProduct from '@/components/CardProduct.vue'
import axios from "axios"

export default {
  name: 'HomeView',
  components: {
    Navbar,
    Hero,
    CardProduct
  },
  data(){
    return{
      product: []
    }
  },
  methods: {
    setProduct(data){
      this.product = data
    }
  },
  mounted(){
    axios
      .get('http://localhost:3000/best-products')
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log("Gagal ", error))
  }
}
</script>
