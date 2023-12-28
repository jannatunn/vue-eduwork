<template>
  <div class="food-detail">
    <Navbar />
    <div class="container">
      <!-- breadcumb -->
      <div class="row mt-4">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item active" area-current="page">
                Food Order
              </li>
            </ol>
          </nav>
        </div>
      </div>

      <!-- product detail -->
      <div class="row mt-3">
        <div class="col-md-6 d-flex">
          <img
            :src="product.product_img"
            alt=""
            class="img-fluid shadow justify-content-center align-items-center rounded"
          />
        </div>

        <div class="col-md-6">
          <h2>
            <strong class="">{{ product.product_name }}</strong>
          </h2>
          <hr />
          <h4>
            Harga : <strong>Rp. {{ product.product_price }}</strong>
          </h4>
          <p>
            Stock : <strong>Rp. {{ product.product_qty_stock }}</strong>
          </p>
          <form class="mt-4" v-on:submit.prevent>
            <div class="form-group my-2">
              <label for="jumlah_pesanan">Jumlah Pesanan</label>
              <input
                type="number"
                class="form-control"
                v-model="pesan.jumlah_pesanan"
              />
            </div>
            <div class="form-group my-2">
              <label for="keterangan">Keterangan</label>
              <textarea
                class="form-control"
                placeholder="keterangan spt : Pedes, Naasi Setengah .."
                v-model="pesan.keterangan"
              ></textarea>
            </div>

            <button type="submit" class="btn btn-success" @click="pemesanan">
              <b-icon-cart></b-icon-cart> Pesan
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/NavbarVue.vue";
import axios from "axios";

export default {
  __name: "ProductDetail",
  components: {
    Navbar,
  },
  data() {
    return {
      product: [],
      pesan: {},
    };
  },
  methods: {
    setProduct(data) {
      this.product = data;
    },
    pemesanan() {
      if (this.pesan.jumlah_pesanan) {
        this.pesan.product = this.product;
        axios
          .post("http://localhost:3000/keranjang", this.pesan)
          .then(() => {
            this.$router.push({ path: "/keranjang" });
            this.$toast.success("Profile saved.", {
              type: "success",
              position: "top-right",
              duration: 3000,
              dismissible: true,
            });
          })
          .catch((error) => console.log(error));
      } else {
        this.$toast.error("jumlah pesanan harus diisi.", {
          type: "error",
          position: "top-right",
          duration: 3000,
          dismissible: true,
        });
      }
    },
  },
  mounted() {
    const apiEndpoint1 =
      "https://sistemtoko.com/public/demo/single/" + this.$route.params.id;
    const apiEndpoint2 =
      "https://sistemtoko.com/public/demo/varian/" + this.$route.params.id;
    axios.all([axios.get(apiEndpoint1), axios.get(apiEndpoint2)]).then(
      axios.spread((response1, response2) => {
        const data1 = response1.data;
        const data2 = response2.data;

        console.log("data 1 product =>", data1)
        console.log("data variant =>", data2)
      })
    );
  },
};
</script>