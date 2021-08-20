<template>
  <section class="menu">
    <span @click="$emit('choose-timer', 'analog')">analog timer</span>
    <span @click="$emit('choose-timer', 'digital')">digital timer</span>
    <span @click="$emit('choose-timer', 'visual')">visual timer</span>
    <span @click="$emit('choose-timer', 'text')">text timer</span>
  </section>
</template>

<script>
export default {
  name: 'Menu',
};
</script>

<style scoped>
.menu {
  width: 100vw;
  height: 100vh;
  z-index: 1900;
  position: absolute;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.8);
  text-transform: uppercase;
  color: white;
  font-family: PT Sans;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
span {
  font-weight: 700;
  margin: 0.5em;
  font-size: 2em;
  cursor: pointer;
}
</style>
