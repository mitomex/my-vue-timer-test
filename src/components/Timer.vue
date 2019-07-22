<template>
  <div>
    <h1>Timer</h1>
    <p>Total: {{ displayNumber }} minute</p>
    <button v-if="!timer" @click="startTimer">再生</button>
    <button v-if="timer" @click="stopTimer">一時停止</button>
    <button @click="resetTimer">停止</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      timer: null,
      totalTime: 1 * 60
    };
  },
  computed: {
    displayNumber() {
      return this.totalTime < 10 ? "0" + this.totalTime : this.totalTime;
    }
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.totalTime--;
      }, 1000);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.timer = null;
    },
    resetTimer() {
      clearInterval(this.timer);
      this.timer = null;
      this.totalTime = 1 * 60;
      alert('Reset timer.')
    }
  },
  watch: {
    totalTime(value) {
      if (value === -1) {
        alert("finish");
        clearInterval(this.timer);
        this.timer = null;
        this.totalTime = 1 * 60;
      }
    }
  }
};
</script>

<style scoped></style>
