<template>
  <div :style="{ minHeight: percentage }"></div>
</template>

<script>
export default {
  props: {
    total: Number,
    minutes: Number,
    seconds: Number,
  },
  computed: {
    timeLeft() {
      return this.minutes * 60 + this.seconds;
    },
    percentage() {
      if (this.timeLeft === 0) return '0vh';
      return (Math.abs(this.timeLeft / this.total - 1) * 100).toFixed(2) + 'vh';
    },
  },
};
</script>

<style scoped>
div {
  width: 100vw;
  background-color: #222;
  z-index: -1;
  transition: all 1s linear;
}
</style>
