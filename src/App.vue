<template>
  <div class="container my-5">
    <ul class="list-group">
      <li class="list-group-item" v-for="(item,index) in items" :key="index">
        {{ item.title }} - {{ item.price }}
      </li>
    </ul>
  </div>
</template>

<script>
import data from "./data";
export default {
  data() {
    return {
      items: [],
    };
  },
  mounted() {
    this.items = data;
  },
};
</script>


<style>

</style>