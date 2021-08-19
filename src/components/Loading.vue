<template>
  <section class="loading-page">
    <svg width="36" height="35" viewBox="0 0 36 35" fill="none" xmlns="http://www.w3.org/2000/svg">
      <rect x="35.5" y="35" width="12" height="35" transform="rotate(-180 35.5 35)" fill="white"/>
      <rect x="20.5" y="35" width="8" height="35" transform="rotate(-180 20.5 35)" fill="white"/>
      <rect x="9.5" y="35" width="4" height="35" transform="rotate(-180 9.5 35)" fill="white"/>
      <rect x="2.5" y="35" width="2" height="35" transform="rotate(-180 2.5 35)" fill="white"/>
    </svg>
    <h2>Interval</h2>
    <p>For all your timing needs</p>
  </section>
</template>

<script>
export default {
  name: 'Loading'
}
</script>

<style scooped>
  @import url('https://fonts.googleapis.com/css2?family=PT+Sans&family=Righteous&display=swap');
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
    z-index: 1000;
    color: white;
    letter-spacing: 2px;
  }
  h2 {
    font-family: Righteous;
    text-transform: uppercase;
    line-height: 2em;
    font-size: 1.8em;
    font-weight: normal;
  }
  p {
    font-family: PT Sans;
  }
</style>