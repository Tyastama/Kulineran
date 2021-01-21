<template>
  <div class="home">
    <Navbar />
    <div class="container">
      <Hero />
      <div class="row mt-4">
        <div class="col">
          <h2>Best <strong>Foods</strong></h2>
        </div>
        <div class="col">
          <router-link to="/foods" class="btn btn-success float-right"
            ><b-icon-eye></b-icon-eye>Lihat Semua</router-link
          >
        </div>
      </div>
      <div class="row mb-4">
        <div class="col-md-4 mt-4" v-for="product in products" :key="product.id">
         <cardProduct :product="product"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import Hero from "@/components/Hero.vue";
import cardProduct from "@/components/cardProduct.vue";
import axios from "axios";
import CardProduct from '../components/cardProduct.vue';

export default {
  name: "Home",
  components: {
    Navbar,
    Hero,
    cardProduct
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProduct(data) {
      this.products = data;
    },
  },
  mounted() {
    // Make a request for a user with a given ID
    axios
      .get("http://localhost:8080/db.json")
      .then((response) => this.setProduct(response.data.best_products))
      .catch((error) => console.log(error))
  },
};
</script>
