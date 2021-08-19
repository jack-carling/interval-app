<template>
  <div id="app">
    <h1>Interval App</h1>
    <SetTimer v-on:startTimer="countDown" />
    <Digital v-bind:timeLeft="timeLeft" />
    <Analog v-bind:seconds="secondsLeft" v-bind:minutes="minutesLeft" />
    <Visual class="visual" v-bind:total="timeTotal" v-bind:seconds="secondsLeft" v-bind:minutes="minutesLeft" />
  </div>
</template>

<script>
import Timer from 'easytimer.js';
import SetTimer from '@/components/SetTimer';
import Digital from '@/components/Digital';
import Analog from '@/components/Analog';
import Visual from '@/components/Visual';

export default {
  components: {
    SetTimer,
    Digital,
    Analog,
    Visual,
  },
  data() {
    return {
      timer: new Timer(),
      timeLeft: '',
      timeTotal: 0,
      minutesLeft: 0,
      secondsLeft: 0,
      showTimer: '',
    };
  },
  methods: {
    countDown(min) {
      this.showTimer = 'visual';
      console.log('in countdown app', min);
      this.timer.start({ countdown: true, startValues: { minutes: min } });
      this.timer.addEventListener('secondsUpdated', () => {
        this.timeLeft = this.timer.getTimeValues().toString(['minutes', 'seconds']);
        this.minutesLeft = this.timer.getTimeValues().minutes;
        this.secondsLeft = this.timer.getTimeValues().seconds;
      });
      this.timeTotal = this.timer.getTimeValues().minutes * 60 + this.timer.getTimeValues().seconds;
      this.timer.addEventListener('targetAchieved', () => {
        //this.timeLeft = "Time´s up";
        //Show Times up-component
      });
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

.visual {
  position: absolute;
  top: 0;
  left: 0;
}
</style>
