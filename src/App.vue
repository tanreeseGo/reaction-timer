<template>
  <h1>ninja reaction timer</h1>
  <p>Click as fast as you can once the box shows up!</p>
  <button @click="start" v-bind:disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" v-bind:delay="delay" @end="endGame" />
  <Results v-if="showResults" v-bind:scoresss="score" />
</template> 

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: { 
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      // console.log(this.delay)
      this.showResults = false
    },
    endGame(myReactionTime) {
      this.score = myReactionTime
      this.isPlaying = false
      this.showResults = true
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
button {
  background: red;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button [disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
