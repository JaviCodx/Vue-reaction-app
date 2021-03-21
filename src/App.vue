<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Start</button>
  <Block v-if="isPlaying" :delay="delay" @end="finish" />
  <Results v-if="showResults" :reactionTime="reactionTime" />
  <Ranking v-if="showResults" :scoreArray="scoreArray" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
import Ranking from "./components/Ranking.vue";

export default {
  name: "App",
  components: {
    Block,
    Results,
    Ranking,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      showResults: false,
      reactionTime: 0,
      scoreArray: [],
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    finish(reactionTime) {
      this.isPlaying = false;
      this.showResults = true;
      this.reactionTime = reactionTime;
      this.scoreArray.push(reactionTime);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

html,
body,
p,
h1 {
  margin: 0;
}

button {
  margin-top: 2em;
  background: #0faf87;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 10px;
  font-size: 1.2rem;
  cursor: pointer;
  letter-spacing: 1px;
}
button:disabled {
  background: rgba(15, 175, 135, 0.5);
}
</style>
