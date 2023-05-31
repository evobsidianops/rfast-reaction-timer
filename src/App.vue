<template>
  <h1>Evobsidianops Reaction Timer</h1>
  <button class="play" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="finalScore" :score="score"/>
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: 0,
      score: null,
      finalScore: false,
    }
  },
  components: { Block, Results },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.finalScore = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.finalScore = true 
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.play {
  background: #0faf87;
  color: white;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  padding:  .7em 2em;
  margin: 10px;
}
.play[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
