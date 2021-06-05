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
  updated() {
    this.heartNumber = this.memeUps;
  },
  data: () => ({
    isFill: false,
    heartNumber: 10,
  }),
  props: {
    memeUps: Number,
  },
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

.heart__count {
  font-size: 1.5rem;
  color: khaki;
}

.fill {
  color: red;
}
</style>