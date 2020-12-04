<template>
  <div>
    <!-- <ul class="list-group">
      <li class="list-group-item" v-for="(item,index) in items" :key="index">
        {{ item.title }} - {{ item.price }}
      </li>
    </ul> -->

    <navbar @search="search"></navbar>

    <div class="container my-5">
      <div class="row">
        <div class="col-md-8">
          <inventory :items="items"  @addtocart="addToCart" ></inventory>
        </div>
        <div class="col-md-4">
         <cart :carts="carts" @remove-item="removeItem" @clear-cart="clearCart"></cart>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import data from "./data";
import Navbar from "./components/Navbar";
import Inventory from './components/Inventory.vue';
import Cart from './components/Cart.vue';
export default {
  data() {
    return {
      items: [],
      carts: [],
    };
  },
  components:{
    Navbar,
    Inventory,
    Cart
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
    },
    clearCart(){
      this.carts = []
    },
    search(keyword){
      this.items = data.filter(item => {
        return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !== -1;
      })
    }
  },

  computed: {
    
  }

};
</script>


<style>
</style>