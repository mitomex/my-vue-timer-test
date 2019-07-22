<template>
  <div>
    <h1>Timer</h1>
    <p>Total: <input class="input" type="text" v-model="totalTime" /> minute</p>
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
      alert("Reset timer.");
    }
  },
  watch: {
    totalTime(value) {
      if (value === 0) {
        alert("finish");
        clearInterval(this.timer);
        this.timer = null;
        this.totalTime = 1 * 60;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.input {
  border-top: 0;
  border-right: 0;
  border-bottom: 1px solid gray;
  border-left: 0;
  box-sizing: border-box;
  font-size: 20px;
  text-align: center;
  width: 60px;
}
</style>
