<template>
  <div>
    <h1>Timer</h1>
    <p>
      <input class="input" type="text" v-model="minute" /> :
      <input class="input" type="text" v-model="second" />
    </p>
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
      minute: 25,
      second: 0
    };
  },
  computed: {},
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        if (this.second < 1) {
          if (this.minute < 1) {
            this.resetTimer();
            return;
          } else {
            this.minute--;
            this.second = 59;
          }
        }
        this.second--;
      }, 1000);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.timer = null;
    },
    resetTimer() {
      alert("Finish");
      clearInterval(this.timer);
      this.timer = null;
      this.second = 60;
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
