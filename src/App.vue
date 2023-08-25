<template>
  <h1>Welcome to the Ninja-Timer</h1>
  <button @click="start" :disabled="isPlaying">PLAY</button>
  <Block v-if="isPlaying" :delay='delay' @end="endGame"/>
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue';
export default {
  name: 'App',
  components:{Block,Results},
  data() {
    return {
      isPlaying: false,
      delay:null,
      score:null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.showResults = false;
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      console.log(this.delay);
    },
    endGame(reactionTime){
      this.score = reactionTime;
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
  color: #444;
  margin-top: 60px;
}
button{
  background: #0faf87;
  color: white;
  border: none;
  padding:8px 16px;
  border-radius: 4px;
  font-size: 1.2em;
  letter-spacing: 1px;
  cursor: pointer;
  margin:10px;
}
button:disabled{
  background: #ccc;
  color: #666;
  cursor: not-allowed;
  opacity: 0.2;
}
</style>
