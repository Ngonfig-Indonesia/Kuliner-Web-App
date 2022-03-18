<template>
  <div class="card shadow card-product">
    <img :src=" 'assets/img/' + products.gambar " class="card-img-top" alt="...">
    <div class="card-body">
        <h5 class="card-title">{{ products.nama }}</h5>
        <p class="card-text">Harga : Rp {{ products.harga }}</p>
        <router-link class="btn btn-primary" :to="'/foods/'+products.id">Pesan</router-link>
    </div>
 </div>
</template>

<script>
export default {
    name: 'CardProduct',
    props: ["products"]
}
</script>

<style>

</style>