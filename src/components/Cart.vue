<template>
  <ul class="list-group">
    <li class="list-group-item bg-dark text-white">
      <strong>Your Shopping </strong>
    </li>
    <li class="list-group-item" v-for="(item, index) in carts" :key="index">
      {{ item.title }} - <strong>${{ item.price }}</strong>
      <span
        class="float-right badge badge-pill badge-danger"
        style="cursor: pointer"
        @click="removeItem(index)"
        >X</span
      >
    </li>
    <li class="list-group-item bg-primary text-white">
      Total Bill: <strong>${{ getTotal.toFixed(2) }}</strong>
    </li>

    <li
      class="list-group-item bg-success text-white text-center mt-5 p-1"
      v-if="carts.length > 0"
    >
      <span style="cursor: pointer" @click="checkout"
        ><strong>Checkout</strong></span
      >
    </li>
  </ul>
</template>

<script>
export default {
  props: ["carts"],
  methods: {
    removeItem(index) {
      this.$emit("remove-item", index);
    },

    checkout() {
      if (confirm("Are you sure to checkout?")) {
        this.$emit("clear-cart");
        alert("Congratulations. You shopping successfully completed");
      }
    },
  },
  computed: {
    getTotal() {
      var total = 0;
      this.carts.forEach((item) => {
        total += parseFloat(item.price);
      });
      return total;
    },
  },
};
</script>

<style>
</style>