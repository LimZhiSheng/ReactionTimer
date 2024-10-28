<template>
  <div v-if="showBlock" class="block" @click="stopTimer">
    <span>Click me!</span>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.showBlock = false;
      this.$emit("end", this.reactionTime / 1000);
    },
  },
};
</script>

<style scoped>
.block {
  width: 100%;
  max-width: 400px;
  border-radius: 15px;
  background: linear-gradient(45deg, #4facfe, #00f2fe);
  color: white;
  text-align: center;
  padding: 80px 0;
  margin: 2rem auto;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.block:hover {
  transform: scale(1.02);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}

.block span {
  font-size: 24px;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 2px;
}
</style>