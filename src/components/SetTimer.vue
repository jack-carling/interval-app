<template>
  <section>
    <button @click="decreaseTime">-</button>
    <span>{{ minutes }}</span>
    <button @click="increaseTime">+</button>
    <button @click="startTimer">Start Timer</button>
  </section>
</template>

<script>
export default {
  name: 'SetTimer',
  data() {
    return {
      minutes: 10
    }
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
    }
  }
}
</script>

<style>

</style>