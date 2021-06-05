<template>
  <div class="container">
    <Logo title="Memeo" />
    <SideBar />
    <Meme />
  </div>
</template>

<script>
import Logo from "./components/Logo.vue";
import SideBar from "./components/SideBar.vue";
import Meme from "./components/Meme.vue";

export default {
  name: "App",
  components: {
    Logo,
    SideBar,
    Meme,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  user-select: none;
}

body {
  display: grid;
  place-items: center;
  color: white;
  background: black;
  overflow-y: hidden;
}

.container {
  position: relative;
  width: 414px;
  max-width: 414px;
  height: 100vh;
}

i {
  transition: all 7ms ease-in-out;
  cursor: pointer;
  font-size: 2.5rem;
}
</style>
