<template>
<div class="food-detail">
  <Navbar />
  <div class="container">
    <!-- breadcrumb -->
    <div class="row mt-4">
      <div class="col mt-3">
        <nav aria-label="breadcrumb">
          <ol class="breadcrumb">
            <li class="breadcrumb-item">
              <router-link to="/">Home</router-link>
            </li>
            <li class="breadcrumb-item">
              <router-link to="/foods">Foods</router-link>
            </li>
            <li class="breadcrumb-item active">Food Order</li>
          </ol>
        </nav>
      </div>
    </div>

    <div class="row mt-3">
      <div class="col-md-6">
          <img :src="'../assets/img/'+product.gambar" class="img-fluid shadow">
      </div>
       <div class="col-md-6">
         <h2><strong>{{ product.nama }}</strong></h2>
         <hr>
         <h4>Harga : <strong>Rp. {{ product.harga }}</strong></h4>
          <form class="mt-3" v-on:submit.prevent>
              <div class="form-group">
                <label for="jumlah_pemesanan">Jumlah Pesan</label>
                <input type="number" class="form-control" v-model="pesan.jumlah_pemesanan" />
              </div>
              <div class="form-group">
                <label for="keterangan">keterangan</label>
                <textarea class="form-control" placeholder="Keterangan Contoh: Pedes, Nasi Sedikit aja" v-model="pesan.keterangan"></textarea>
              </div>
              <button type="submit" class="btn btn-primary" @click="pemesanan">Pesan</button>
          </form>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
import axios from 'axios'
export default {
    name: "FoodDetail",
    components: {
      Navbar,
    },
    data(){
      return {
        product: [],
        pesan: {}
      }
    },
    methods: {
       setProduct(data){
         this.product = data;
       },
       pemesanan(){
         this.pesan.products = this.product; 
         axios
          .post("http://localhost:3000/keranjangs", this.pesan)
          .then(() => {
            app.$toast.success('Sukses Masuk Keranjang', {
               type: 'success',
               position: 'top-right',
               duration: 3000,
            })
          })
          .catch((err) => console.log(err));
       }
    },
    mounted(){
      axios
        .get('http://localhost:3000/products/'+this.$route.params.id)
        .then((response) => this.setProduct(response.data))
        .catch((error) => console.log("Gagal ", error))
    }
}
</script>

<style>

</style>