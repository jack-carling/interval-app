<template>
  <div id="app">
    <img class="nav" :src="getNavIcon()" alt="" @click="showMenu = !showMenu" />
    <Menu v-if="showMenu" @choose-timer="chooseTimer" />
    <SetTimer v-if="showTimer === ''" @start-timer="countDown" />
    <Digital v-if="showTimer === 'digital'" :timeLeft="timeLeft" />
    <Analog
      v-if="showTimer === 'analog'"
      v-bind:seconds="secondsLeft"
      v-bind:minutes="minutesLeft"
    />
    <Visual
      v-if="showTimer === 'visual'"
      class="visual"
      v-bind:total="timeTotal"
      v-bind:seconds="secondsLeft"
      v-bind:minutes="minutesLeft"
    />
    <button class="abort">abort timer</button>
  </div>
</template>

<script>
import Timer from 'easytimer.js';
import SetTimer from '@/components/SetTimer';
import Digital from '@/components/Digital';
import Analog from '@/components/Analog';
import Visual from '@/components/Visual';
import Menu from '@/components/Menu';

export default {
  components: {
    SetTimer,
    Digital,
    Analog,
    Visual,
    Menu,
  },
  data() {
    return {
      timer: new Timer(),
      timeLeft: '',
      timeTotal: 0,
      minutesLeft: 0,
      secondsLeft: 0,
      showTimer: '',
      preferredTimer: 'digital',
      showMenu: false,
    };
  },
  methods: {
    countDown(payload) {
      this.showTimer = 'visual';
      console.log('in countdown app', payload.minutes);
      this.timer.start({
        countdown: true,
        startValues: { minutes: payload.minutes },
      });
      this.timer.addEventListener('secondsUpdated', () => {
        this.timeLeft = this.timer
          .getTimeValues()
          .toString(['minutes', 'seconds']);
        this.minutesLeft = this.timer.getTimeValues().minutes;
        this.secondsLeft = this.timer.getTimeValues().seconds;
      });
      this.timeTotal =
        this.timer.getTimeValues().minutes * 60 +
        this.timer.getTimeValues().seconds;
      this.timer.addEventListener('targetAchieved', () => {
        //this.timeLeft = "Time´s up";
        //Show Times up-component
      });
      this.showTimer = this.preferredTimer;
      console.log('<app>intervalbox ', payload.intervalBox);
      console.log('<app>breakbox ', payload.breakBox);
    },
    getNavIcon() {
      const icon = require.context('./assets/', false, /\.svg$/);
      return icon(`./nav-${this.showMenu ? 'white' : 'black'}.svg`);
    },
    chooseTimer(type) {
      this.showMenu = false;
      this.preferredTimer = type;
      if (this.showTimer) this.showTimer = type;
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=PT+Sans&family=Righteous&display=swap');
* {
  box-sizing: border-box;
}
body {
  margin: 0;
  padding: 0;
  background-color: #e5e5e5;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.visual {
  position: absolute;
  top: 0;
  left: 0;
}
.nav {
  position: absolute;
  top: 1em;
  left: 1em;
  z-index: 2000;
  cursor: pointer;
}
.abort {
  padding: 0.3em 0.5em;
  text-transform: uppercase;
  border: 1px solid #888;
  font-size: 1em;
  font-family: 'PT Sans';
  font-weight: bold;
  letter-spacing: 0.1em;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom: 3em;
  border-radius: 5px;
  background-color: #e5e5e5;
  color: #888;
}
</style>
