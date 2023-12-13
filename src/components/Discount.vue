<template>
  <article class="discount">
    <h4>지금 사면 {{ disPer }}% SALE</h4>
  </article>
</template>

<script>
export default {
  name: "DiscountBanner",
  data() {
    return {};
  },
  props: {
    disPer: Number,
  },
};
</script>

<style>
</style>