<template>
  <div>
    <div>
      <h1>{{ formatTime }}</h1>
      <button v-if="!isRunning" @click="start">Start</button>
      <button v-if="isRunning" @click="stop">Stop</button>
      <button @click="reset">Reset</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      startTime: null,
      stopTime: null,
      elapsedTime: 0,
    };
  },
  computed: {
    isRunning() {
      return this.startTime !== null;
    },
    formatTime() {
      const date = new Date(this.elapsedTime);
      const minutes = date.getUTCMinutes().toString().padStart(2, "0");
      const seconds = date.getUTCSeconds().toString().padStart(2, "0");
      const milliseconds = Math.floor(date.getUTCMilliseconds() / 10)
        .toString()
        .padStart(2, "0");
      return `${minutes}:${seconds}.${milliseconds}`;
    },
  },
  methods: {
    start() {
      this.startTime = new Date();
      this.timer = setInterval(this.updateTime, 10);
    },
    stop() {
      clearInterval(this.timer);
      this.stopTime = new Date();
      this.elapsedTime += this.stopTime - this.startTime;
      this.startTime = null;
    },
    reset() {
      clearInterval(this.timer);
      this.startTime = null;
      this.stopTime = null;
      this.elapsedTime = 0;
    },
    updateTime() {
      this.elapsedTime = new Date() - this.startTime;
    },
  },
};
</script>

<style scoped></style>
