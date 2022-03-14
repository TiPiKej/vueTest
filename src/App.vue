<template>
  <h1>Reaction timer</h1>
  <button :disabled="gameIsOn" @click="playTheGame">Play</button>
  <Block v-if="blockVisible" @end="gameIsOver" />
  <Result v-else-if="delay" :delay="delay" />
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  data() {
    return {
      gameIsOn: false,
      blockVisible: false,
      startTime: 0,
      endTime: 0,
    }
  },
  methods: {
    playTheGame() {
      this.gameIsOn = true;
      setTimeout(() => {
        this.blockVisible = true;
        this.startTime = new Date();
      }, this.random(500, 5000))
    },
    gameIsOver() {
      this.gameIsOn = false;
      this.blockVisible = false;
      this.endTime = new Date();
    },
    random(min = 1, max = 10) {
      return Math.random() * (max - min) + min
    }
  },
  components: { Block, Result },
  computed: {
    delay() {
      return this.endTime.valueOf() - this.startTime.valueOf()
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

button {
  background: #43a047;
  color: white;
  padding: 10px 20px;
  font-size: 1.1rem;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  margin: 20px;
}

button:hover {
  background: #388e3c;
}

button:disabled {
  cursor: unset;
  background: gray;
}

</style>
