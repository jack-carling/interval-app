<template>
  <div id="app">
    <h1>Interval App</h1>
    <!--<button @click="decreaseTime">-</button>
    <span>{{ minutes }}</span>
    <button @click="increaseTime">+</button>
    <p>{{ timeLeft }}</p>
    <hr>-->
    <SetTimer v-on:startTimer="countDown" />
    <Digital v-bind:timeLeft="timeLeft" />

    <!--<p>{{ timeLeft }}</p>-->
  </div>
</template>

<script>
import Timer from 'easytimer.js';
import SetTimer from '@/components/SetTimer';
import Digital from '@/components/Digital';

export default {
  components: {
    SetTimer,
    Digital
  },
  data() {
    return {
      timer: new Timer(),
      minutes: 10,
      timeLeft: '',
    };
  },
  methods: {
    decreaseTime() {
      if (this.minutes > 1) {
        this.minutes--;
      }
    },
    increaseTime() {
      if (this.minutes < 59) {
        this.minutes++;
      }
    },
    countDown(min) {
      console.log('in countdown app', min);
      this.minutes = min;
      this.timer.start({ countdown: true, startValues: { minutes: this.minutes }});
      this.timer.addEventListener('secondsUpdated', () => {
        this.timeLeft = this.timer.getTimeValues().toString();
      });
      this.timer.addEventListener('targetAchieved', () => {
        //this.timeLeft = "Time´s up";
        //Show Times up-component
      });
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
