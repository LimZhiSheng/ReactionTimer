<template>
  <div class="results">
    <h2>Your Result</h2>
    <p class="score">{{ score.toFixed(3) }} seconds</p>
    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 0.25) {
      this.rank = "Lightning Fast! 🚀";
    } else if (this.score < 0.4) {
      this.rank = "Quick Reflexes! 👍";
    } else {
      this.rank = "Keep Practicing! 💪";
    }
  },
};
</script>

<style scoped>
.results {
  background-color: #f0f8ff;
  border-radius: 10px;
  padding: 1.5rem;
  margin-top: 2rem;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

h2 {
  color: #333;
  margin-bottom: 1rem;
}

.score {
  font-size: 2.5rem;
  font-weight: bold;
  color: #4facfe;
  margin-bottom: 0.5rem;
}

.rank {
  font-size: 1.4rem;
  color: #333;
  font-weight: bold;
}
</style>