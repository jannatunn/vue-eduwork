<template>
  <div class="card">
    <h5 class="card-title p-2">{{ product.name }}</h5>
    <img :src="product.photo" class="card-img-top" alt="gambar" />
    <div class="card-body">
      <div class="d-flex justify-content-between">
        <p class="">Stock :</p>
        <p class=" ">Rp. {{ product.price }}</p>
      </div>
      <!-- Tambahkan tombol untuk memicu tampilan modal -->
      <router-link
        :to="`/product/` + product.id"
        class="btn btn-primary float-end"
        ><b-icon-cart></b-icon-cart> Pesan</router-link
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: ["product"],
};
</script>