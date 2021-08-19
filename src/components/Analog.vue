<template>
  <div class="clock">
    <div ref="minutes" class="minutes"></div>
    <div class="circle"></div>
    <div ref="seconds" class="seconds"></div>
  </div>
</template>

<script>
export default {
  props: {
    minutes: Number,
    seconds: Number,
  },
  watch: {
    minutes() {
      const degree = (this.minutes / 60) * 360;
      this.$refs.minutes.style.transform = `rotate(${degree}deg)`;
    },
    seconds() {
      const degree = (this.seconds / 60) * 360;
      this.$refs.seconds.style.transform = `rotate(${degree}deg)`;
      if (this.seconds === 59) {
        this.$refs.seconds.style.transition = 'none';
      } else {
        this.$refs.seconds.style.transition = 'all 0.3s linear';
      }
    },
  },
};
</script>

<style scoped>
div.clock {
  width: 200px;
  height: 200px;
  position: relative;
  background-image: url('../assets/frame.svg');
  background-size: cover;
}
div.minutes {
  height: 82px;
  width: 0;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 86px;
  left: 0;
  margin: auto;
  border: 2px solid #000;
  background-color: #000;
  border-radius: 999px;
  transform-origin: bottom;
  transform: rotate(0deg);
  transition: all 0.3s linear;
}
div.seconds {
  height: 82px;
  width: 0;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 86px;
  left: 0;
  margin: auto;
  border: 2px solid #555;
  background-color: #555;
  border-radius: 999px;
  transform-origin: bottom;
  transform: rotate(0deg);
}
div.circle {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  position: absolute;
  border: 3px solid #000;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  background-color: #555;
}
</style>
