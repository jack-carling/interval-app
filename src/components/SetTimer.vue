<template>
  <section class="setTimer">
    <section class="minutes-container">
      <span @click="decreaseTime" class="decrease"
        ><img src="../assets/left-chevron.svg" alt=""
      /></span>

      <article class="minutes">
        <h1>{{ minutes }}</h1>
        <p>minutes</p>
      </article>
      <span @click="increaseTime" class="increase">
        <img src="../assets/right-chevron.svg" alt="" />
      </span>
    </section>
    <section class="checkboxes">
      <label class="container">
        <input type="checkbox" v-model="intervalBox" />
        <span class="checkmark"></span>
        intervals
      </label>
      <br />
      <label class="container">
        <input type="checkbox" v-model="breakBox" />
        <span class="checkmark"></span>
        5 min break / interval
      </label>
      <br />
      <button @click="startTimer">Start Timer</button>
    </section>
  </section>
</template>

<script>
export default {
  name: 'SetTimer',
  data() {
    return {
      minutes: 10,
      intervalBox: false,
      breakBox: false,
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
      let payload = {
        minutes: this.minutes,
        intervalBox: this.intervalBox,
        breakBox: this.breakBox,
      };
      this.$emit('start-timer', payload);
    },
  },
  watch: {
    intervalBox(value) {
      if (value) this.breakBox = false;
    },
    breakBox(value) {
      if (value) this.intervalBox = false;
    },
  },
};
</script>

<style>
.setTimer {
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1000;
  color: #222222;
  letter-spacing: 2px;
  font-family: PT Sans;
}
.setTimer h1 {
  line-height: 0em;
  font-size: 5em;
}
.minutes-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  height: 10em;
  width: 65vw;
}
.minutes {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  height: 6em;
}
.minutes h1 {
  line-height: 0em;
  font-size: 5em;
  margin: 20px 0;
}
.minutes p {
  margin: 0;
  padding: 0;
  line-height: 0;
  color: #888888;
}
.checkboxes {
  width: 80vw;
  position: absolute;
  bottom: 3em;
}
.checkboxes button {
  width: 100%;
  padding: 0.3em;
  text-transform: uppercase;
  border: 1px solid #222;
  font-size: 1.8em;
  font-family: 'PT Sans';
  font-weight: 700;
  letter-spacing: 2px;
  margin-top: 1em;
  border-radius: 5px;
  background-color: #e5e5e5;
}
.container {
  display: block;
  position: relative;
  padding-left: 45px;
  margin-bottom: 0;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default checkbox */
.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  background-color: #e5e5e5;
  border: 1px solid #222;
  border-radius: 3px;
}

/* When the checkbox is checked, add a blue background */
.container input:checked ~ .checkmark {
  background-color: #222;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: '';
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.container input:checked ~ .checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.container .checkmark:after {
  left: 8px;
  top: 3px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
</style>
