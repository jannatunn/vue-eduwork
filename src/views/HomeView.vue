<template>
  <div>
    <Navbar />
    <div class="container">
      <Hero />
      <div class="row">
        <div class="col-md-3" v-for="product in products" :key="product.id">
          <CardProduct :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import Navbar from "@/components/NavbarVue.vue";
import CardProduct from "@/components/CardProduct.vue";
import Hero from "@/components/HeroVue.vue";
import axios from "axios";

export default {
  name: "HomeView",
  components: {
    Navbar,
    CardProduct,
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
