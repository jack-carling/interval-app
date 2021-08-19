<template>
  <section>
    <button @click="decreaseTime">-</button>
    <span>{{ minutes }}</span>
    <button @click="increaseTime">+</button>
    <button @click="startTimer">Start Timer</button>

    <input type="checkbox" />
    <span>intervals</span>
    <input type="checkbox" />
    <span>5 min break / intervals</span>
  </section>
</template>

<script>
export default {
  name: 'SetTimer',
  data() {
    return {
      minutes: 10,
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
    startTimer() {
      console.log(this.minutes);
      this.$emit('startTimer', this.minutes);
    },
  },
};
</script>

<style></style>
