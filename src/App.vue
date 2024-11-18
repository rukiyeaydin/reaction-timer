<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">PLAY</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      // console.log(this.delay);
      this.showResults = false;
      
    },
    endGame(reactionTime){
      this.score = reactionTime,
      this.isPlaying = false;
      this.showResults = true;
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
  color: #2c3e50;
  margin-top: 60px;
}
button{
  padding: 10px 20px;
  background-color: #45b66e;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:disabled{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
