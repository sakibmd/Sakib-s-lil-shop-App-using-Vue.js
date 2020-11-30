<template>
  <div>
    <!-- <ul class="list-group">
      <li class="list-group-item" v-for="(item,index) in items" :key="index">
        {{ item.title }} - {{ item.price }}
      </li>
    </ul> -->

    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <a class="navbar-brand" href="#">Sakib's Shop</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto"></ul>
        <form class="form-inline my-2 my-lg-0">
          <input
            class="form-control mr-sm-2"
            type="search"
            placeholder="Search"
            aria-label="Search"
          />
          <button class="btn btn-outline-success my-2 my-sm-0" type="submit">
            Search
          </button>
        </form>
      </div>
    </nav>

    <div class="container my-5">
      <div class="row">
        <div class="col-md-8">
          <div class="row">
           <div class="col-md-4 mb-4" v-for="(item,index) in items" :key="index">
              <div class="card">
              <img :src="item.photo" class="card-img-top" />
              <div class="card-body">
                <h5 class="card-title">{{ item.title }}</h5>
                <h5>Price: <strong>${{item.price}}</strong></h5>
<hr>
                <a @click="addToCart(item)" class="btn btn-info">Add to card</a>
              </div>
            </div>
           </div>

          </div>
        </div>
        <div class="col-md-4">
          <ul class="list-group">
            <li class="list-group-item bg-dark text-white">
              <strong>Your Shopping </strong>
            </li>
            <li class="list-group-item" v-for="(item,index) in carts" :key="index">
              {{ item.title }} - <strong>${{ item.price }}</strong>
              <span class="float-right badge badge-pill badge-danger" style="cursor:pointer" @click="removeItem(index)">X</span>
            </li>
            <li class="list-group-item bg-success text-white">
              Total Bill: <strong>${{ getTotal.toFixed(2) }}</strong>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import data from "./data";
export default {
  data() {
    return {
      items: [],
      carts: [],
    };
  },
  mounted() {
    this.items = data;
  },
  methods: {
    addToCart(item){
      this.carts.push(item);
    },

    removeItem(index){
      this.carts.splice(index, 1);
    }
  },

  computed: {
    getTotal(){
      var total = 0;
      this.carts.forEach(item => {
        total += parseFloat(item.price)
      });
      return total;
    }
  }

};
</script>


<style>
</style>