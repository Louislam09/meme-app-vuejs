<template>
  <div class="sidebar__container">
    <div class="sidebar__top">
      <div class="sidebar__item">
        <Profile />
      </div>
      <div class="sidebar__item">
        <Reload />
      </div>
      <div class="sidebar__item">
        <Sound />
      </div>
      <div class="sidebar__item">
        <PosterProfile />
      </div>
      <div class="sidebar__item">
        <Heart />
      </div>
    </div>
  </div>
</template>

<script>
import Profile from "./sidebar/Profile";
import Reload from "./sidebar/Reload";
import Sound from "./sidebar/Sound";
import PosterProfile from "./sidebar/PosterProfile";
import Heart from "./sidebar/Heart";

export default {
  name: "SideBar",
  components: {
    Profile,
    Reload,
    Sound,
    PosterProfile,
    Heart,
  },
};
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

  width: 100%;
  height: 100%;
  /* border: 1px solid white; */
}

.sidebar__item {
  margin-bottom: 2rem;
}
</style>