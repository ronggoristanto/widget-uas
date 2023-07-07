<template>
  <div>
    <h2>Stopwatch Widget</h2>
    <div>{{ displayTime }}</div>
    <button @click="startStopwatch">Start</button>
    <button @click="stopStopwatch">Stop</button>
    <button @click="resetStopwatch">Reset</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      displayTime: '00:00:00',
      timer: null,
      startTime: null
    }
  },
  methods: {
    startStopwatch() {
      if (!this.timer) {
        this.startTime = Date.now();
        this.timer = setInterval(this.updateStopwatch, 1000);
      }
    },
    stopStopwatch() {
      clearInterval(this.timer);
      this.timer = null;
    },
    resetStopwatch() {
      clearInterval(this.timer);
      this.timer = null;
      this.displayTime = '00:00:00';
      this.startTime = null;
    },
    updateStopwatch() {
      const currentTime = Date.now();
      const elapsedTime = currentTime - this.startTime;
      const seconds = Math.floor(elapsedTime / 1000) % 60;
      const minutes = Math.floor(elapsedTime / 1000 / 60) % 60;
      const hours = Math.floor(elapsedTime / 1000 / 60 / 60);
      this.displayTime = `${this.formatTime(hours)}:${this.formatTime(minutes)}:${this.formatTime(seconds)}`;
    },
    formatTime(time) {
      return String(time).padStart(2, '0');
    }
  }
}
</script>
