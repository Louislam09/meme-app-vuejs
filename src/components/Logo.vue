<template>
  <div class="title">{{ title }}</div>
</template>

<script>
export default {
  name: "Logo",
  props: {
    title: String,
  },
};
</script>

<style scoped>
.title {
  position: absolute;
  left: 10px;
  top: 10px;
  z-index: 99;
  width: fit-content;
  color: khaki;
  font-size: 2rem;
  font-weight: bold;
  text-shadow: 1px 1px 1px black;
  animation: blink 5s ease-in-out infinite alternate;
  transition: all 2ms ease;
}

@keyframes blink {
  from {
    transform: rotate(0deg) scale(1);
  }
  to {
    transform: rotate(360deg) scale(0);
  }
}
</style>