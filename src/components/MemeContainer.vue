<template>
  <div class="meme__container" ref="mContainer">
    <Meme :imageUrl="defaultImage" :title="'default'" v-show="loading" />
    <Meme
      v-for="({ url }, index) in memeData"
      :key="index"
      :imageUrl="url"
      :title="index.toString()"
    />
  </div>
</template>

<script>
import Meme from "./Meme.vue";
import { onCreate, i as cIndex } from "../utils/swipe";

// getComputedStyle(document.documentElement)
//     .getPropertyValue('--my-variable-name')

export default {
  name: "MemeContainer",
  beforeUpdate() {
    onCreate(this.data.length, this.setCurrentMeme);
    if (this.data.length > 0) {
      this.loading = false;
      this.memeData = this.data;
    }
  },
  props: {
    data: Array,
    setCurrentMeme: Function,
  },
  data() {
    return {
      memeData: [],
      loading: true,
      defaultImage: "http://placehold.it/210x140?text=N/A",
      currentMemeIndex: 0,
    };
  },
  methods: {
    // updateMemeIndex(number) {
    //   console.log(number);
    //   this.currentMemeIndex = number;
    // },
  },
  components: {
    Meme,
  },
};
</script>

<style scoped>
.meme__container {
  /* --n: 1;
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
  transition: transform calc(var(--f) * 0.5s) cubic-bezier(1, 1.59, 0.61, 0.74); */

  --n: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  overflow-y: hidden;
  width: 100%;
  height: 100%;
  height: calc(var(--n) * 100%);

  transform: translate(
    0,
    calc(var(--tx, 0px) + var(--i, 0) / var(--n) * -100%)
  );
}

.smooth {
  transition: transform calc(var(--f, 1) * 0.5s) ease-out;
}

img {
  width: 100%;
  height: 731px;
  height: calc(100% / var(--n));
  object-fit: contain;
  pointer-events: none;
  /* background-color: gray; */
  /* border: 4px solid red; */
}
</style>