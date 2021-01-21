<template>
  <div class="card shadow card-product">
      <img :src="'/assets/images/' + product.gambar " class="card-img-top" alt=""/>
      <div class="card-body">
          <h5 class="card-title">{{product.nama}}</h5>
          <p class="card-text">Harga : Rp. {{product.harga}}</p>
          <a href="#" class="btn btn-success" @click="addtoCart(product)"><b-icon-cart></b-icon-cart>Pesan</a>
      </div>
  </div>
  
</template>

<script>
export default {
  name: "cardProduct",
  props: ["product"],
  methods: {
    addtoCart(item){
      let cart = []
      if (localStorage.getItem('cart')){
        cart = JSON.parse(localStorage.getItem('cart'))
        cart.push(item)
        localStorage.setItem("cart",JSON.stringify(cart));
        return
      }
     cart.push(item)
      localStorage.setItem("cart",JSON.stringify(cart));
    }
  }
};
</script>

<style>
</style>