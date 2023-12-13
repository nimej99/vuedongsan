<template>
  <section>
    <Menu />

    <Discount v-if="discount" :disPer="disPer" />

    <button @click="basicSort()">기본값정렬</button>
    <button @click="priceSort()">가격순정렬</button>

    <!-- :class="{클래스명:조건}" -->
    <!-- <div class="start" :class="{ end: modal }"> -->
    <Transition name="fade">
      <Modal
        :products="products"
        :modal="modal"
        :modalId="modalId"
        @modalClose="modalClose()"
        @report="report($event)"
      />
    </Transition>
    <!-- </div> -->

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
      discount: true,
      disPer: 30,
      modal: false,
      modalId: 0,
      productsOriginal: [...data],
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
    basicSort() {
      this.products = [...this.productsOriginal];
    },
    priceSort() {
      this.products.sort((a, b) => a.price - b.price);
    },
  },
  // lifecycle hooks
  /*
    beforeCreate()
    created()
    beforeMount()
    mounted
    beforeUpdate()
    updated()
    beforeUnmount()
    unmounted()
    등등
  */
  created() {
    // ajax 요청시 created, mounted 에 데이터 요청 넣음
  },
  mounted() {
    let Timer = setInterval(() => {
      if (this.disPer > 10) {
        this.disPer -= 5;
      }
      if (this.disPer == 10) {
        this.discount = false;
      }
    }, 1000);

    if (this.disPer == 10) {
      clearInterval(Timer);
    }
    // setTimeout(() => {
    //   this.discount = false;
    // }, 2000);
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

.start {
  opacity: 0;
  transition: all 1s;
}
.end {
  opacity: 1;
}

/* 등장 애니메이션 = name속성명-enter-from, active, to */
/* 시작스타일 */
.fade-enter-from {
  opacity: 0;
}
/* transition */
.fade-enter-active {
  transition: all 1s;
}
/* 끝날때스타일 */
.fade-enter-to {
  opacity: 1;
}
/* 퇴장 애니메이션 = name속성명-leave-from, active, to */
</style>
