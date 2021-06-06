<template>
  <div
    class="meme__container"
    ref="containerRef"
    @mousedown="lock"
    @mousemove="drag"
    @mouseup="move"
  >
    <Meme :meme="state.defatulMeme" v-show="state.loading" />
    <Meme
      v-for="(meme, index) in state.memeDataComputed"
      :key="index"
      :meme="meme"
    />
  </div>
</template>

<script setup>
import Meme from "./Meme.vue";
import {
  computed,
  defineProps,
  reactive,
  watchEffect,
  ref,
  watch,
  onMounted,
} from "@vue/runtime-core";

const containerRef = ref(null);

let y0 = null;
let i = 0;
let locked = false;
let h;

const props = defineProps({
  data: Array,
  fetchMeme: Function,
});

const state = reactive({
  memeData: props.data,
  loading: true,
  defatulMeme: {
    author: "Testing",
    ups: 0,
    url: "http://placehold.it/210x140?text=state.numberOfItem/A",
  },
  numberOfItem: computed(() => {
    return state.memeData.length;
  }),
  memeDataComputed: computed(() => {
    return state.memeData;
  }),
});

watchEffect(() => {
  if (containerRef.value) {
    state.memeData = props.data;
    state.loading = false;
    containerRef.value.style.setProperty("--n", state.numberOfItem);
  }
});

// watch(() => {
//   if (props.data.length > 0 && state.firstTime) {
//     state.loading = false;
//     state.firstTime = false;
//     state.memeData = props.data;
//   }
// });
// onCreate();

const loadMoreMeme = async (index) => {
  if (index == 4) {
    const dd = await props.fetchMeme();
    state.memeData.push(...dd);
  }
};

function size() {
  h = window.innerHeight;
}

onMounted(onCreate);

function onCreate() {
  console.log("mounted is ok");
  containerRef.value.addEventListener("touchstart", lock, false);
  containerRef.value.addEventListener("touchend", move, false);
  containerRef.value.addEventListener("touchmove", drag, false);
}

size();
addEventListener("resize", size, false);

function unify(e) {
  return e.changedTouches ? e.changedTouches[0] : e;
}

function lock(e) {
  y0 = unify(e).clientY;
  containerRef.value.classList.toggle("smooth", !(locked = true));
}

function move(e) {
  if (locked) {
    let dy = unify(e).clientY - y0;
    let s = Math.sign(dy);
    let f = +((s * dy) / h).toFixed(2);

    if ((i > 0 || s < 0) && (i < state.numberOfItem - 1 || s > 0) && f > 0.2) {
      containerRef.value.style.setProperty("--i", (i -= s));
      let canFetchNumber = state.numberOfItem - i;
      loadMoreMeme(canFetchNumber);
      f = 1 - f;
    }
    containerRef.value.style.setProperty("--ty", "0px");
    containerRef.value.style.setProperty("--f", f);
    containerRef.value.classList.toggle("smooth", !(locked = false));
    y0 = null;
  }
}

function drag(e) {
  e.preventDefault();
  if (locked) {
    containerRef.value.style.setProperty(
      "--ty",
      `${Math.round(unify(e).clientY - y0)}px`
    );
  }
}
</script>

<style scoped>
.meme__container {
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

.meme__container > div {
  width: 100%;
  height: 731px;
  height: calc(100% / var(--n));
}
</style>