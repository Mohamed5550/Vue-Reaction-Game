<template>
  <h1>Ninja Reaction Timer</h1>
  <button class="button" @click="startGame" :disabled="isPlaying">Start</button>
  <Result v-if="showResult" :score="score"/>
  <Box v-if="isPlaying" :delay="time" @end="endGame"/>
</template>

<script>
import Result from './components/Result.vue'
import Box from './components/Box.vue'

export default {
  name: 'App',
  components: {
    Result,
    Box
  },
  data() {
    return {
      isPlaying: 0,
      time: 0,
      showResult: 0,
      score: 0
    }
  },
  methods: {
    startGame() {
        if(this.isPlaying) return;
        this.showResult = 0;
        this.isPlaying = 1;
        this.time = 2000 + Math.random() * 5000;
    },
    endGame(reactionTime) {
      this.isPlaying = 0;
      this.showResult = 1;
      this.score = reactionTime;
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

.button {
  padding: 10px 20px;
  border-radius: 10px;
  border: 0;
  color: #FFF;
  font-size: 20px;
  cursor: pointer;
  background: #0faf87;
}

.button[disabled] {
  background: #0faf8740;
}
</style>
