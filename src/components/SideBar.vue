<template>
  <div class="sidebar__container">
    <div class="sidebar__top">
      <div class="sidebar__item">
        <Profile :authorName="meme && meme.author" />
      </div>
      <div class="sidebar__item">
        <ShareIcon />
      </div>
      <div class="sidebar__item">
        <DownloadIcon />
      </div>
      <div class="sidebar__item">
        <Heart :memeUps="meme && meme.ups" />
      </div>
    </div>
  </div>
</template>

<script setup>
import Profile from "./sidebar/Profile";
import Heart from "./sidebar/Heart";
import ShareIcon from "./sidebar/ShareIcon";
import DownloadIcon from "./sidebar/DownloadIcon";
import { defineProps } from "vue";

const props = defineProps({
  meme: Object,
});
</script>

<style scoped>
.sidebar__container {
  position: absolute;
  z-index: 99;
  width: fit-content;
  top: 0;
  right: 0;
  height: 100%;
  padding: 1rem 0.5rem 0 0;

  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: space-between;
}

.sidebar__top {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  width: 100%;
  height: 100%;
  /* border: 1px solid white; */
}

.sidebar__item {
  margin-bottom: 2rem;
}
</style>