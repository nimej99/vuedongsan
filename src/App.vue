<template>
  <div>
    <nav class="menu">
      <a href="" v-for="(a, i) in index" :key="i">{{ a }}</a>
    </nav>

    <img alt="Vue logo" src="./assets/logo.png" />

    <div v-for="(data, index) in 3" :key="index">
      <h4>{{ products.title[index] }}</h4>
      <p>{{ products.price[index] }}</p>
      <button @click="increase(index)">허위매물신고</button>
      <span>신고수 : {{ products.reportCount[index] }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  //데이터 보관함
  data() {
    return {
      index: ["Home", "About", "Products"],
      products: {
        title: ["역삼동원룸", "마포구원룸", "천호동원룸"],
        price: [50, 60, 70],
        reportCount: [0, 0, 0],
      },
    };
  },
  methods: {
    increase(index) {
      this.products.reportCount[index]++;
    },
  },

  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
