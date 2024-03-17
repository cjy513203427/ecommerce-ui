<template>
  <div id="home">
    <div id="background-div" class="page-holder bg-cover">
        <div class="container py-5">
        <header class="text-left text-white py-5">
          <h3 class="mb-4 rounded"><a href="#start-shopping" class="bg-white px-2 py-2 rounded" id="heading">Start Shopping</a></h3>
          <p id="content" class="lead mb-0 bg-dark p-1 rounded">E-commerce demo project</p>
        </header>
      </div>
    </div>
  </div>

  <div id="start-shopping" class="container">
    <div class="row">
      <div class="col-12 text-left">
        <h2 class="pt-3">Top Categories</h2>
      </div>
    </div>

    <div class="row">
      <div v-for="index in this.category_size" :key="index" class="col-md-6 col-xl-4 col-12 pt-3  justify-content-around d-flex">
        <CategoryBox :category="categories[index-1]">
        </CategoryBox>
      </div>
    </div>
  </div>

  <div class="container">
    <div class="row">
      <div class="col-12 text-left">
        <h2 class="pt-3">Top Products</h2>
      </div>
    </div>
    <div class="row">
      <div v-for="index in this.product_size" :key="index" class="col-md-6 col-xl-4 col-12 pt-3  justify-content-around d-flex">
        <ProductBox :product="products[index-1]">
        </ProductBox>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';
  import ProductBox from '../components/Product/ProductBox.vue'
  import CategoryBox from "../components/Cateogry/CategoryBox.vue";
  export default {
    name: 'Home',
    components : {CategoryBox, ProductBox},
    props : ["baseURL", "products", "categories"],
    data(){
      return{
        baseURL: "http://localhost:8081",
        category_size:0
      }
    },
    mounted(){
      if (this.categories && this.categories.length > 0) {
        this.category_size = Math.min(6, this.categories.length);
      } else {
        console.error('Categories data is null or empty.');
      }

      this.product_size = this.products.length;
      this.product_size = Math.min(8, this.product_size);

    }
  }
</script>

<style>
  .page-holder {
    min-height: 100vh;
  }

  #background-div {
    background: url(../assets/home.png)
  }

  .bg-cover {
    background-size: cover !important;
  }

  #heading {
    text-decoration: none;
    font-family: 'Roboto', sans-serif;
    font-weight: 400;
    opacity: 0.8;
    font-family: 'Josefin Sans', sans-serif;
  }
</style>