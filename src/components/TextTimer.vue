<template>
  <section class="text">
    <h1>
      {{ minutesText[minutes] }} <span> {{ singleMinute }} </span> och
      {{ secondsText[seconds] }} <span> {{ singleSecond }} </span> kvar
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

  computed: {
    singleMinute() {
      if (this.minutes == 1) {
        return 'minut'
      } else {
        return 'minuter'
      }
    },

    singleSecond() {
      if (this.seconds == 1) {
        return 'sekund'
      } else {
        return 'sekunder'
      }
    },
  },
}
</script>

<style scoped>
.text {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.text h1 {
  font-size: 3.5em;
  padding: 2rem;
  text-transform: uppercase;
}
</style>
