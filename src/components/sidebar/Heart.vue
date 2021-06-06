<template>
  <div class="heart__container">
    <div>
      <i class="bx bxs-heart fill" v-if="isFill" @click="toggleHeart"></i>
      <i class="bx bx-heart" v-else @click="toggleHeart"></i>
    </div>
    <div class="heart__count">
      {{ heartNumber }}
    </div>
  </div>
</template>

<script setup>
import { defineProps, reactive } from "@vue/runtime-core";

const props = defineProps({
  memeUps: Number,
});

let { isFill, heartNumber } = reactive({
  isFill: false,
  heartNumber: 0,
});

heartNumber = props.memeUps || 0;

const toggleHeart = () => {
  isFill = !isFill;
  isFill ? (heartNumber += 1) : (heartNumber -= 1);
};
</script>

<style scoped>
.heart__container {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.heart__count {
  font-size: 1.5rem;
  color: black;
  color: red;
}

.fill {
  color: red;
}
</style>