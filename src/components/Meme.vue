<template>
  <div class="meme__container">
    <!-- <img
      src="https://i.redd.it/bevha2alw4171.jpg"
      alt="meme3"
      class="meme__image"
    />
     -->
    <img
      v-for="({ url }, index) in memes"
      :key="index"
      :src="url"
      :alt="index"
      class="meme__image"
    />
  </div>
</template>

<script>
import meme1 from "../assets/images/1.jpg";
import meme2 from "../assets/images/2.jpg";
import meme3 from "../assets/images/3.png";
import { onCreate, memes } from "../utils/swipe";

export default {
  name: "meme1",
  data: () => ({
    images: [
      "https://i.redd.it/bevha2alw4171.jpg",
      "https://i.redd.it/9irjbw3dbs071.jpg",
      "https://i.redd.it/tqkj7z1a7p071.jpg",
      "https://i.redd.it/r66a9y2hv4171.jpg",
      "https://i.redd.it/jw7t9jwztu071.jpg",
      "https://i.redd.it/tqr49nkjto171.jpg",
      "https://i.redd.it/owe2chhduo171.jpg",
    ],
    memes,
    image1: meme1,
    image2: meme2,
    image3: meme3,
  }),
  methods: {},
  mounted() {
    onCreate();
  },
};
</script>

<style scoped>
.meme__container {
  --n: 1;
  --i: 0;

  display: flex;
  flex-direction: column;
  width: 100%;
  height: calc(var(--n) * 100%);

  overflow-y: hidden;
  transform: translate(
    0,
    calc(var(--i, 0) / var(--n) * -100% + var(--ty, 0px))
  );
  transition: transform calc(var(--f) * 0.5s) cubic-bezier(1, 1.59, 0.61, 0.74);
}

.smooth {
  transition: transform calc(var(--f, 1) * 0.5s) ease-out;
}

img {
  width: 100%;
  min-height: 731px;
  height: calc(100% / var(--n));
  object-fit: contain;
  pointer-events: none;
  background-color: gray;
}
</style>