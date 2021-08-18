<template>
  <div id="app">
    <h1>Interval App</h1>
    <button @click="decreaseTime">-</button>
    <span>{{ time }}</span>
    <button @click="increaseTime">+</button>
    <p>{{ timeLeft }}</p>
  </div>
</template>

<script>
import Timer from 'easytimer.js';

export default {
  data() {
    return {
      timer: new Timer(),
      time: 10,
      timeLeft: '',
    };
  },
  methods: {
    decreaseTime() {
      if (this.time > 1) {
        this.time--;
      }
    },
    increaseTime() {
      if (this.time < 59) {
        this.time++;
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
