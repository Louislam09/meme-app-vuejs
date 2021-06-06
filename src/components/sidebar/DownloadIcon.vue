<template>
  <i class="bx bxs-download"></i>
</template>

<script>
export default {
  name: "DownloadIcon",
  data: () => ({}),
  methods: {
    onDownload() {},
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