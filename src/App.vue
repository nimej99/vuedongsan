<template>
  <section>
    <Menu />
    <Discount />
    <Modal
      :products="products"
      :modal="modal"
      :modalId="modalId"
      @modalClose="modalClose()"
      @report="report($event)"
    />
    <Card
      :data="products[index]"
      v-for="(data, index) in products"
      :key="index"
      @modalOpen="modalOpen($event)"
    />
  </section>
</template>

<script>
import data from "./assets/data/oneroom.js";
import Menu from "./components/Menu.vue";
import Discount from "./components/Discount.vue";
import Modal from "./components/Modal.vue";
import Card from "./components/Card.vue";

export default {
  name: "App",
  //데이터 보관함
  data() {
    return {
      modal: false,
      modalId: 0,
      products: data,
      // [
      //   {
      //     title: "성내동원룸",
      //     price: 50,
      //     report: 0,
      //     img: require("./assets/images/room0.jpg"),
      //   },
      //   {
      //     title: "혜화동원룸",
      //     price: 60,
      //     report: 0,
      //     img: require("./assets/images/room1.jpg"),
      //   },
      //   {
      //     title: "연희동원룸",
      //     price: 70,
      //     report: 0,
      //     img: require("./assets/images/room2.jpg"),
      //   },
      // ],
    };
  },
  methods: {
    modalClose() {
      this.modal = false;
    },
    modalOpen(e) {
      this.modal = true;
      this.modalId = e;
    },
    report(e) {
      this.products[e].report += 1;
    },
  },

  components: {
    Discount: Discount,
    Menu,
    Modal,
    Card,
  },
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
body {
  margin: 0;
}
div {
  box-sizing: border-box;
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

.room-img {
  width: 100%;
  margin-top: 40px;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
  box-sizing: border-box;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
