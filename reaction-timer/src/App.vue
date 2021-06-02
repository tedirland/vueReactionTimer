<template>
<div>
<h1> Ninja Reaction Timer </h1>
<button @click="start" :disabled="isPlaying"> Play</button>
<Block v-if="isPlaying" :delay="delay" @end="endGame" />
<Results v-if="score" :score="score"  />

</div>
</template>

<script>
import Block from './components/Block'

import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {Block, Results},
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,

    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying=true;
      this.score= null
    },
    endGame(reactionTime) {
    this.score = reactionTime
    console.log(this.score)
    this.isPlaying = false

    }
  }
}
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
</style>
