<template>
  <div class="row">
    <div class="col-md-4 mb-4" v-for="(item, index) in items" :key="index">
      <div class="card">
        <img :src="item.photo" class="card-img-top" />
        <div class="card-body">
          <h5 class="card-title">{{ item.title }}</h5>
          <h5>
            Price: <strong>${{ item.price }}</strong>
          </h5>
          <hr />
          <button class="btn btn-sm btn-info" @click="addToCart(item)">Add to card</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["items"],
  methods: {
    addToCart(item) {
      this.$emit("addtocart", item);
    },
  },
};
</script>

<style>
</style>