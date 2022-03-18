<template>
  <div class="hero">

      <!-- Desktop -->
      <div class="d-none d-md-block">
          <div class="row mt-3">
            <div class="col-md-6">
                <div class="d-flex h-100">
                    <div class="justify-content-center align-self-center">
                        <h2><strong>Delecious Food Menu</strong><br> In Your Gadget</h2>
                        <p>Segera Pesan Makanan Favorit Anda</p>
                        <router-link class="btn btn-warning" to="/foods">Pesan</router-link>
                    </div>
                </div>
            </div>
            <div class="col-md-6">
                <img src="../assets/img/banner.png" class="banner">
            </div>
        </div>
      </div>
      <!-- Mobile -->
      <div class="d-sm-block d-md-none">
          <div class="row mt-3">
              <div class="col-md-6">
                <img src="../assets/img/banner.png" class="banner">
            </div>
            <div class="col-md-6">
                <div class="d-flex h-100">
                    <div class="justify-content-center align-self-center">
                        <h2><strong>Delecious Food Menu</strong><br> In Your Gadget</h2>
                        <p>Segera Pesan Makanan Favorit Anda</p>
                        <button class="btn btn-warning">Pesan</button>
                    </div>
                </div>
            </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    name: "Hero"
}
</script>

<style>

</style>