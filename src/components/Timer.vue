<template>
  <div>
    <p>Total: {{ displayNumber }}</p>
    <button @click="startTimer">再生</button>
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
