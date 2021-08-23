<template>
  <section class="digital">
    <h1>
      {{ minutesText[minutes] }} <span ref="toSingleMinute"></span> och
      {{ secondsText[seconds] }} <span ref="toSingleSecond"></span> kvar
    </h1>
  </section>
</template>

<script>
export default {
  name: 'TextTimer',
  props: {
    minutes: Number,
    seconds: Number,
  },
  data() {
    return {
      secondsText: [
        'noll',
        'en',
        'två',
        'tre',
        'fyra',
        'fem',
        'sex',
        'sju',
        'åtta',
        'nio',
        'tio',
        'elva',
        'tolv',
        'tretton',
        'fjorton',
        'femton',
        'sexton',
        'sjutton',
        'arton',
        'nitton',
        'tjugo',
        'tjugoen',
        'tjugotvå',
        'tjugotre',
        'tjugofyra',
        'tjugofem',
        'tjugosex',
        'tjugosju',
        'tjugoåtta',
        'tjugonio',
        'trettio',
        'trettioen',
        'trettiotvå',
        'trettiotre',
        'trettiofyra',
        'trettiofem',
        'trettiosex',
        'trettiosju',
        'trettioåtta',
        'trettionio',
        'fyrtio',
        'fyrtioen',
        'fyrtiotvå',
        'fyrtiotre',
        'fyrtiofyra',
        'fyrtiofem',
        'fyrtiosex',
        'fyrtiosju',
        'fyrtioåtta',
        'fyrtionio',
        'femtio',
        'femtioen',
        'femtiotvå',
        'femtiotre',
        'femtiofyra',
        'femtiofem',
        'femtiosex',
        'femtiosju',
        'femtioåtta',
        'femtionio',
      ],

      minutesText: [
        'noll',
        'en',
        'två',
        'tre',
        'fyra',
        'fem',
        'sex',
        'sju',
        'åtta',
        'nio',
        'tio',
        'elva',
        'tolv',
        'tretton',
        'fjorton',
        'femton',
        'sexton',
        'sjutton',
        'arton',
        'nitton',
        'tjugo',
        'tjugoen',
        'tjugotvå',
        'tjugotre',
        'tjugofyra',
        'tjugofem',
        'tjugosex',
        'tjugosju',
        'tjugoåtta',
        'tjugonio',
        'trettio',
        'trettioen',
        'trettiotvå',
        'trettiotre',
        'trettiofyra',
        'trettiofem',
        'trettiosex',
        'trettiosju',
        'trettioåtta',
        'trettionio',
        'fyrtio',
        'fyrtioen',
        'fyrtiotvå',
        'fyrtiotre',
        'fyrtiofyra',
        'fyrtiofem',
        'fyrtiosex',
        'fyrtiosju',
        'fyrtioåtta',
        'fyrtionio',
        'femtio',
        'femtioen',
        'femtiotvå',
        'femtiotre',
        'femtiofyra',
        'femtiofem',
        'femtiosex',
        'femtiosju',
        'femtioåtta',
        'femtionio',
      ],
    }
  },
  watch: {
    minutes() {
      this.handleSingleMinute()
    },
    seconds() {
      this.handleSingleSecond()
    },
  },
  methods: {
    handleSingleMinute() {
      if (this.minutes == 1) {
        this.$refs.toSingleMinute.innerText = 'minut'
      } else {
        this.$refs.toSingleMinute.innerText = 'minuter'
      }
    },

    handleSingleSecond() {
      if (this.seconds == 1) {
        this.$refs.toSingleSecond.innerText = 'sekund'
      } else {
        this.$refs.toSingleSecond.innerText = 'sekunder'
      }
    },
  },
}
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
  text-transform: uppercase;
}
</style>
