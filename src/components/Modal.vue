<template>
  <div v-if="modal == true" class="black-bg">
    <div class="white-bg">
      <img
        :src="products[modalId].img"
        :alt="products[modalId].title"
        class="room-img"
      />
      <h4>{{ products[modalId].title }}</h4>
      <span>{{ products[modalId].content }}</span>
      <p>{{ products[modalId].price }}원</p>

      <button @click="report()">허위매물신고</button>
      <span>신고수 : {{ products[modalId].report }}</span>

      <button @click="modalClose()">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "modalView",
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