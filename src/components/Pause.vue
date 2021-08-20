<template>
  <section class="times-up">
    <img src="../assets/pause.svg" alt="" />
    <h1>Pause &amp; breath</h1>
    <p>{{ timeLeft }}</p>
    <button @click="$emit('reset-timer')" class="new-time">
      no pause, go now!
    </button>
  </section>
</template>

<script>
import Timer from 'easytimer.js';

export default {
  name: 'Pause',
  data() {
    return {
      timer: new Timer(),
      timeLeft: '05:00',
    };
  },
  mounted() {
    this.timer.start({
      countdown: true,
      startValues: { minutes: 5 },
    });
    this.timer.addEventListener('secondsUpdated', () => {
      this.timeLeft = this.timer
        .getTimeValues()
        .toString(['minutes', 'seconds']);
    });
    this.timer.addEventListener('targetAchieved', () => {
      this.$emit('reset-timer');
    });
  },
};
</script>

<style scoped>
p {
  color: #888;
  font-size: 1.5em;
}
</style>
