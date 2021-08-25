<template>
  <section class="digital">
    <h1>{{ timeLeft }}</h1>
  </section>
</template>

<script>
export default {
  name: 'Digital',
  props: {
    timeLeft: String,
  },
};
</script>

<style scoped>
.digital {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.digital h1 {
  font-size: 4em;
  letter-spacing: 0.1em;
}
</style>
