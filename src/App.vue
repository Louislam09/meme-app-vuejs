<template>
  <div class="container">
    <Logo title="Memeo" />
    <SideBar :memeUps="memeUps" />
    <MemeContainer :data="memes" :setCurrentMeme="setCurrentMeme" />
  </div>
</template>

<script>
import Logo from "./components/Logo.vue";
import SideBar from "./components/SideBar.vue";
import MemeContainer from "./components/MemeContainer.vue";
const apiUrl = "https://meme-api.herokuapp.com/gimme";
const goodSubReddits = [
  "ahorasinllorar",
  "yo_elvr",
  "espanol",
  "orslokx",
  "vicio",
  "MemesEnEspanol",
  "MemesESP",
  "memessanos",
];

const regularSubReddits = [
  "spanish",
  "SpanishMeme",
  "memeshumedos",
  "MemesEnEspanol",
  "Webadas",
  "orslokx",
  "MexicanMemes",
  "espanol",
  "Dominican",
  "ahorasinllorar",
];

const getRandomFrom = (arr) => {
  return Math.floor(Math.random() * arr.length);
};

const fetchMeme = async () => {
  const gSubReddit = goodSubReddits[getRandomFrom(goodSubReddits)];
  const rSubReddit = regularSubReddits[getRandomFrom(regularSubReddits)];
  const sr = Math.floor(Math.random() * 2);
  const selected = sr == 0 ? gSubReddit : rSubReddit;

  const res = await fetch(`${apiUrl}/${selected}/30`);
  const results = await res.json();
  const { memes } = await results;
  console.log(selected);
  return memes;
};

export default {
  name: "App",
  components: {
    Logo,
    SideBar,
    MemeContainer,
  },
  data: () => ({
    memes: [],
    memeUps: 0,
  }),
  async created() {
    const dd = await fetchMeme();
    this.memes = dd;
  },
  methods: {
    setCurrentMeme(number) {
      this.memeUps = this.memes[number].ups;
      console.log(this.memeUps);
    },
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
  /* background: #00000086; */
  /* background: linear-gradient(to bottom, pink, orange); */
  background: rgb(238, 174, 202);
  background: radial-gradient(
    circle,
    rgba(238, 174, 202, 1) 0%,
    rgba(148, 187, 233, 1) 100%
  );
  overflow-y: hidden;
}

.container {
  /* position: relative; */
  width: auto;
  max-width: 614px;
  height: 100vh;
  /* border: 1px solid red; */
}

i {
  transition: all 7ms ease-in-out;
  cursor: pointer;
  font-size: 2.5rem;
  color: khaki;
  font-weight: bold;
}
</style>
