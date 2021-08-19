<template>
  <div class="clock">
    <div class="minutes"></div>
    <div class="seconds"></div>
  </div>
</template>

<script>
export default {
  props: {
    minutes: Number,
    seconds: Number,
  },
};
</script>

<style scoped>
div.clock {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  border: 3px solid #333;
  position: relative;
}
div.minutes {
  height: 100px;
  position: absolute;
  top: 0%;
  left: 50%;
  border: 2px solid blue;
  transform-origin: bottom;
  transform: rotate(0deg);
}
div.seconds {
  width: 60px;
  position: absolute;
  top: 50%;
  left: 50%;
  border: 1px solid orange;
  transform-origin: 0%;
  transform: rotate(200deg);
}
</style>
