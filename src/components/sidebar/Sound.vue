<template>
  <i class="bx bx-volume-full" v-if="isSound" @click="toggleSound"></i>
  <i class="bx bx-volume-mute" v-else @click="toggleSound"></i>
</template>

<script>
export default {
  name: "Sound",
  data: () => ({
    isSound: false,
  }),
  methods: {
    toggleSound() {
      this.isSound = !this.isSound;
    },
  },
};
</script>

<style>
</style>