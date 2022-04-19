<template>
  <h1>REACTION TIMER</h1>
  <button @click="start" :disabled="isPlayng">play</button>
  <Result v-if="showResults" :score="score" />
  <Block v-if="isPlayng" :delay="delay" @end="endGame" />
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return {
      isPlayng: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlayng = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlayng = false
      this.showResults =true
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
  color: #444;
  margin-top: 60px;
}
.pole {
  width: 1200px;
  height: 600px;
}
button {
  background: rgb(30, 118, 90);
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
