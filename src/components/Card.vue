<template>
  <article>
    <img
      :src="data.img"
      :alt="data.title"
      @click="modalOpen()"
      class="room-img"
    />
    <h4 @click="modalOpen()">
      {{ data.title }}
    </h4>
    <p>{{ data.price }}원</p>
  </article>
</template>

<script>
export default {
  name: "roomCard",
  props: {
    data: Object,
  },
  methods: {
    modalOpen() {
      this.$emit("modalOpen", this.data.id);
    },
  },
};
</script>

<style>
</style>