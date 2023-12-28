<template>
  <div class="card">
    <img :src="product.photo" class="card-img-top" alt="gambar" />
  </div>
</template>

<script>
export default {
  name: "GaleryCard",
  props: ["product"],
};
</script>