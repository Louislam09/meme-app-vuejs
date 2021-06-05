<template>
  <div class="heart__container">
    <div>
      <i class="bx bxs-heart fill" v-if="isFill" @click="toggleHeart"></i>
      <i class="bx bx-heart" v-else @click="toggleHeart"></i>
    </div>
    <div class="heart__count">
      {{ heartNumber }}
    </div>
  </div>
</template>

<script>
export default {
  name: "Heart",
  data: () => ({
    isFill: false,
    heartNumber: 10,
  }),
  methods: {
    toggleHeart() {
      this.isFill = !this.isFill;
      this.isFill ? (this.heartNumber += 1) : (this.heartNumber -= 1);
    },
  },
};
</script>

<style scoped>
.heart__container {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.fill {
  color: red;
}
</style>