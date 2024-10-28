<template>
  <div class="container">
    <h1>Reaction Timer Challenge</h1>
    <button class="button" @click="start" :disabled="isPlaying">
      {{ isPlaying ? 'Get Ready...' : 'Start Game' }}
    </button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Result v-if="showResult" :score="score" />
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Results.vue";

export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.showResult = true;
      this.isPlaying = false;
    },
  },
};
</script>

<style>
body {
  background-image: linear-gradient(to right, #4facfe 0%, #00f2fe 100%);
  margin: 0;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: 'Arial', sans-serif;
}

.container {
  background-color: rgba(255, 255, 255, 0.9);
  border-radius: 15px;
  padding: 2rem;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
  text-align: center;
  max-width: 500px;
  width: 90%;
}

h1 {
  color: #333;
  margin-bottom: 1.5rem;
}

.button {
  background: #4facfe;
  color: white;
  border: none;
  padding: 12px 24px;
  border-radius: 25px;
  font-size: 18px;
  font-weight: bold;
  letter-spacing: 1px;
  cursor: pointer;
  transition: all 0.3s ease;
  margin: 1rem 0;
}

.button:hover:not(:disabled) {
  background: #00f2fe;
  transform: translateY(-2px);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
}

.button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>