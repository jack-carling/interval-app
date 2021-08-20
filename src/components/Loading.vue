<template>
  <section class="loading-page">
    <img src="../assets/logo.svg" alt="" />
    <h2>Interval</h2>
    <p>For all your timing needs</p>
  </section>
</template>

<script>
export default {
  name: 'Loading',
};
</script>

<style scoped>
.loading-page {
  height: 100vh;
  width: 100vw;
  background-color: black;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 5000;
  color: white;
  letter-spacing: 2px;
}
h2 {
  font-family: Righteous;
  text-transform: uppercase;
  line-height: 0;
  font-size: 1.8em;
  font-weight: normal;
}
p {
  line-height: 0;
}
</style>
