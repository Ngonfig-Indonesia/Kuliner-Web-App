<template>
  <div class="">
      <Navbar />
      <div class="container">
          <div class="row mt-3">
              <div class="col">
                  <h2>Daftar <strong>Makanan</strong></h2>
              </div>
          </div>
          <div class="row mt-3">
              <div class="col">
                  <div class="input-group mb-3">
                    <input v-model="search" type="text" class="form-control" placeholder="Cari Makanan Kesukaan mu.." aria-label="Username" aria-describedby="basic-addon1" @keyup="searchFood">
                    <span class="input-group-text" id="basic-addon1">Cari</span>
                  </div>
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
import Navbar from '@/components/Navbar.vue'
import CardProduct from '@/components/CardProduct.vue'
import axios from "axios"

export default {
    name: "Food",
    components: {
        Navbar,
        CardProduct,
    },
    data(){
    return{
      product: [],
      search: '',
    }
    },
    methods: {
        setProduct(data){
        this.product = data
        },
        searchFood(){
            axios
            .get('http://localhost:3000/products?q='+this.search)
            .then((response) => this.setProduct(response.data))
            .catch((error) => console.log("Gagal ", error))
        }
    },
    mounted(){
        axios
        .get('http://localhost:3000/products')
        .then((response) => this.setProduct(response.data))
        .catch((error) => console.log("Gagal ", error))
    }
}
</script>

<style>

</style>