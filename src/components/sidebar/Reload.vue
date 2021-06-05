<template>
  <i
    class="bx bxs-chevron-down animated-down"
    v-if="showDown"
    @click="toggleDown"
  ></i>
  <i class="bx bx-repost" v-else @click="toggleDown"></i>
</template>

<script>
export default {
  name: "Reload",
  data: () => ({
    showDown: false,
  }),
  methods: {
    toggleDown() {
      this.showDown = !this.showDown;
    },
  },
};
</script>

<style scoped>
.animated-down {
  animation: down 1.5s ease infinite alternate;
}

@keyframes down {
  0% {
    transform: translateY(10px);
  }
  100% {
    transform: translateY(0px);
  }
}
</style>