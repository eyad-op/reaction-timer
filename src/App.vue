<template>
  <h1>Reaction Timer Game</h1>
  <button @click="startGame" :disabled="isPlaying">Start Playing</button>
  <Block v-if="isPlaying" :delay="delay" @gameEnd="gameEnd" />
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from "@/components/Block.vue";
import Results from "@/components/Results.vue";
export default {
  name: "App",
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      showResults: false,
      score: null,
    };
  },
  methods: {
    startGame() {
      this.delay = 1000 + Math.random() * 6000;
      this.isPlaying = true;
      this.showResults = false;
    },
    gameEnd(reactionTime) {
      this.score = reactionTime;
      this.showResults = true;
      this.isPlaying = false;
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
button {
  padding: 1rem 2rem;
  background-color: crimson;
  color: aliceblue;
  font-size: 1rem;
  font-weight: 600;
  border: none;
  outline: none;
  border-radius: 0.5rem;
  cursor: pointer;
  letter-spacing: 1px;
}
button[disabled] {
  background-color: rgba(220, 20, 60, 0.247);
  cursor: not-allowed;
}
</style>
