<template>
  <img class="meme__image" :src="imageUrl" :alt="title" />
</template>

<script>
export default {
  name: "Meme",
  props: {
    imageUrl: String,
    title: String,
  },
};
</script>

<style scoped>
img {
  width: 100%;
  height: 731px;
  height: calc(100% / var(--n));
  object-fit: contain;
  pointer-events: none;
  background: radial-gradient(
    circle,
    rgba(238, 174, 202, 1) 0%,
    rgba(148, 187, 233, 1) 100%
  );
}
</style>