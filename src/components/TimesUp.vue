<template>
  <section class="times-up">
    <img src="../assets/bell.svg" alt="" />
    <h1>Time's up!</h1>
    <button @click="$emit('reset-timer')" class="new-time">
      set new timer
    </button>
  </section>
</template>

<script>
export default {
  name: 'TimesUp',
};
</script>

<style scoped></style>
