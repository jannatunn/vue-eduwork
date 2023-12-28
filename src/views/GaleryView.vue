<template>
  <div>
    <Navbar />
    <div class="container">
      <Hero />
      <div class="row">
        <div class="col-md-3 g-3" v-for="product in products" :key="product.id">
          <GaleryProduct :product="product"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import Navbar from "@/components/NavbarVue.vue";
import GaleryProduct from "@/components/GaleryProduct.vue"
import Hero from "@/components/HeroVue.vue";
import axios from "axios";

export default {
  name: "HomeView",
  components: {
    Navbar,
    GaleryProduct,
    Hero,
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProducts(data) {
      this.products = data;
    },
  },
  mounted() {
    axios
      .get("https://sistemtoko.com/public/demo/product")
      .then((res) => this.setProducts(res.data.aaData))
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped>
.hover:hover {
  transform: scale(1.1);
  transition: transform 1.5s ease;
  z-index: 999;
}
</style>