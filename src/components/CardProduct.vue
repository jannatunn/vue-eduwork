<template>
  <div class="card">
    <h5 class="card-title p-2">{{ product.name }}</h5>
    <img :src= 'product.photo' class="card-img-top" alt="gamabr" />
    <div class="card-body">
      <div class="d-flex justify-content-between">
        <p class="">Stock :</p>
        <p class=" ">Rp. {{ product.price }}</p>
      </div>
      <a href="#" class="btn btn-primary float-end">beli</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: ["product"],
};
</script>