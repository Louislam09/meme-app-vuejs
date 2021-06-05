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
  color: rgb(95, 0, 139);
  font-size: 2rem;
  font-weight: bold;
  text-shadow: 1px 1px 1px black;
}
</style>