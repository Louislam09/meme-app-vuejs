<template>
  <div class="profile__container">
    <div>
      <i class="bx bx-user-circle"></i>
    </div>
    <div class="profile__name">
      {{ authorName || "-" }}
    </div>
  </div>
</template>

<script>
export default {
  name: "Profile",
  props: {
    authorName: String,
  },
};
</script>

<style scoped>
.profile__container {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.profile__name {
  font-size: 1.5rem;
  color: red;
}
</style>