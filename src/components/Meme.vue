<template>
  <div class="meme__content">
    <SideBar :meme="state.defatulMeme" />
    <img class="meme__image" :src="state.defatulMeme.url" :alt="title" />
  </div>
</template>

<script setup>
import { defineProps, reactive } from "vue";
import SideBar from "./SideBar.vue";

const props = defineProps({
  meme: Object,
});

const state = reactive({
  defatulMeme: {
    author: "Testing",
    ups: 0,
    url: "http://placehold.it/210x140?text=N/A",
  },
});

state.defatulMeme = props.meme;
</script>

<style scoped>
.meme__content {
  position: relative;
}

img {
  border: 2px solid white;
  width: 100%;
  /* height: 731px; */
  height: 100%;
  object-fit: contain;
  pointer-events: none;
  background: radial-gradient(
    circle,
    rgba(238, 174, 202, 1) 0%,
    rgba(148, 187, 233, 1) 100%
  );
}
</style>