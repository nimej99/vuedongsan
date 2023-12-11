<template>
  <nav class="menu">
    <a href="" v-for="(a, i) in nav" :key="i">{{ a }}</a>
  </nav>
</template>

<script>
export default {
  name: "mainMenu",
  data() {
    return {
      nav: ["Home", "About", "Products"],
    };
  },
};
</script>

<style>
</style>