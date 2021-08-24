<template>
  <div id="app">
    <section class="topbar">
      <img
        class="nav"
        :src="getNavIcon()"
        alt=""
        @click="showMenu = !showMenu"
      />
      <p class="title">interval</p>
    </section>
    <transition name="fade">
      <Loading v-if="showLoading" @click.native="showLoading = false" />
    </transition>
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
    <TextTimer
      v-if="showTimer === 'text'"
      :seconds="secondsLeft"
      :minutes="minutesLeft"
    />

    <button @click="handleAbort" class="abort">abort timer</button>
    <TimesUp v-if="showTimesUp" @reset-timer="handleReset" />
    <Pause v-if="showPause" @reset-timer="handlePause" />
  </div>
</template>

<script>
import Timer from 'easytimer.js';
import SetTimer from '@/components/SetTimer';
import Digital from '@/components/Digital';
import Analog from '@/components/Analog';
import Visual from '@/components/Visual';
import TextTimer from '@/components/TextTimer';
import Menu from '@/components/Menu';
import TimesUp from '@/components/TimesUp';
import Pause from '@/components/Pause';
import Loading from '@/components/Loading';

export default {
  components: {
    SetTimer,
    Digital,
    Analog,
    Visual,
    TextTimer,
    Menu,
    TimesUp,
    Pause,
    Loading,
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
      showTimesUp: false,
      showPause: false,
      savedStartTime: 0,
      showLoading: true,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showLoading = false;
    }, 2000);
  },
  methods: {
    countDown(payload) {
      this.showTimer = 'visual';
      console.log('in countdown app', payload.minutes);
      this.savedStartTime = payload.minutes;
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
        if (payload.intervalBox) {
          // handle interval
          this.timer.start({
            countdown: true,
            startValues: { minutes: payload.minutes },
          });
          return;
        } else if (payload.breakBox) {
          // handle break
          this.showPause = true;
          return;
        } else {
          // handle time's up
          this.showTimesUp = true;
        }
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
    handleAbort() {
      this.showTimer = '';
      this.timer.stop();
      this.timeLeft = '';
      this.timeTotal = 0;
      this.minutesLeft = 0;
      this.secondsLeft = 0;
      this.preferredTimer = 'digital';
    },
    handleReset() {
      this.handleAbort();
      this.showTimesUp = false;
    },
    handlePause() {
      this.timer.start({
        countdown: true,
        startValues: { minutes: this.savedStartTime },
      });
      this.showPause = false;
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
  font-family: PT Sans;
  color: #222;
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
.topbar {
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  z-index: 2000;
  width: 100vw;
}
.title {
  left: 50%;
  transform: translateX(-50%);
  position: absolute;
  letter-spacing: 0.1em;
}
.nav {
  padding: 1em;
  cursor: pointer;
}
.fade-leave-active {
  transition: opacity 1s;
}
.fade-leave-to {
  opacity: 0;
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
  background-color: transparent;
  color: #888;
}
button {
  cursor: pointer;
}
/** overlays */
.times-up {
  width: 100vw;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  background: radial-gradient(#383837, #222);
  background: radial-gradient(
        farthest-side,
        rgba(255, 255, 255, 0.04) 100%,
        transparent
      )
      center center/150px 150px,
    radial-gradient(farthest-side, rgba(255, 255, 255, 0.03) 100%, transparent)
      center center/240px 240px,
    radial-gradient(farthest-side, rgba(255, 255, 255, 0.02) 100%, transparent)
      center center/380px 380px,
    radial-gradient(farthest-side, rgba(255, 255, 255, 0.02) 100%, transparent)
      center center/600px 600px,
    radial-gradient(farthest-side, #222 96%, #222) center center/100% 100%;
  background-repeat: no-repeat;
  z-index: 3000;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: white;
  letter-spacing: 0.1em;
}
.times-up h1 {
  font-size: 2rem;
  margin-top: 2rem;
  position: absolute;
  bottom: 7em;
  letter-spacing: 0.1em;
  font-weight: bold;
}
.times-up p {
  position: absolute;
  bottom: 7.5em;
}
.new-time {
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
  color: #888;
  background-color: transparent;
}
</style>
