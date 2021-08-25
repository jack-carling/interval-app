<template>
  <section class="analog">
    <div class="clock">
      <div class="circle"></div>
      <div ref="minutes" class="minutes"></div>
      <div ref="seconds" class="seconds"></div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    minutes: Number,
    seconds: Number,
  },
  watch: {
    minutes() {
      this.handleMinutes();
    },
    seconds() {
      this.handleSeconds();
    },
  },
  methods: {
    handleMinutes() {
      const degree = (this.minutes / 60) * 360;
      this.$refs.minutes.style.transform = `rotate(${degree}deg)`;
    },
    handleSeconds() {
      const degree = (this.seconds / 60) * 360;
      this.$refs.seconds.style.transform = `rotate(${degree}deg)`;
      if (this.seconds === 59) {
        this.$refs.seconds.style.transition = 'none';
      } else {
        this.$refs.seconds.style.transition = 'all 1s linear';
      }
    },
  },
  mounted() {
    this.handleSeconds();
    this.handleMinutes();
  },
};
</script>

<style scoped>
.analog {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
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
  transition: all 0.5s linear;
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
  z-index: 2;
}
div.circle {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  position: absolute;
  border: 1px solid #000;
  z-index: 1;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  background-color: #555;
}
</style>
