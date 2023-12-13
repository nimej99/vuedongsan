<template>
  <div v-if="modal == true" class="black-bg">
    <div class="white-bg">
      <img
        :src="products[modalId].img"
        :alt="products[modalId].title"
        class="room-img"
      />
      <h4>{{ products[modalId].title }}</h4>
      <p>{{ products[modalId].content }}</p>
      <!-- <input type="text" @input="month = $event.target.value" /> -->
      <input type="text" v-model.number="month" />
      <p>{{ month }}개월 {{ month * products[modalId].price }}원</p>

      <button @click="report()">허위매물신고</button>
      <span>신고수 : {{ products[modalId].report }} </span>

      <button @click="modalClose()">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "modalView",
  data() {
    return {
      month: 1,
    };
  },
  // 데이터 감시 후 함수 실행 유즈이펙트?
  watch: {
    month(e) {
      if (e > 12) {
        alert("12개월 이내로 선택해주세요.");
        this.month = 1;
      }
      if (isNaN(e) == true) {
        alert("숫자만 입력해주세요.");
        this.month = 1;
      }
    },
  },
  props: {
    products: Array,
    modal: Boolean,
    modalId: Number,
  },
  methods: {
    report() {
      this.$emit("report", this.modalId);
    },
    modalClose() {
      this.$emit("modalClose");
    },
  },
};
</script>

<style>
</style>