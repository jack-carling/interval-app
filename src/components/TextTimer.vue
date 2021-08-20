<template>
  <section class="digital">
    <h1> {{this.minutes}}: {{this.seconds}} / {{minutesText[minutes]}} : {{secondsText[seconds]}}</h1>
    <!-- <h1> {{this.minutes}}: {{this.seconds}} / {{this.minutesText[this.minutes]}} : {{this.secondsText[this.seconds]}}</h1> -->
  </section>
</template>

<script>
export default {
name: 'TextTimer',
 props: {
    minutes: Number,
    seconds: Number
  },
data() {
    
    return {
        secondsText :["noll", "ett", "två","tre","fyra", "fem","sex", "sju", "åtta", "nio","tio", "elva", "tolv", "tretton", "fjorton", "femton", "sexton", "sjutton", "arton", "nitton",  
        "tjugo", "tjugoett", "tjugotvå", "tjugotre", "tjugofyra", "tjugofem", "tjugosex", "tjugosju", "tjugoåtta", "tjugonio",
        "trettio","trettioett", "trettiotvå", "trettiotre", "trettiofyra", "trettiofem", "trettiosex", "trettiosju", "trettioåtta", "trettionio", 
        "fyrtio", "fyrtioett","fyrtiotvå","fyrtiotre","fyrtiofyra","fyrtiofem","fyrtiosex","fyrtiosju","fyrtioåtta","fyrtionio",
        "femtio", "femtioett", "femtiotvå", "femtiotre", "femtiofyra", "femtiofem", "femtiosex", "femtiosju", "femtioåtta", "femtionio",],

        minutesText :["noll", "ett", "två","tre","fyra", "fem","sex", "sju", "åtta", "nio","tio", "elva", "tolv", "tretton", "fjorton", "femton", "sexton", "sjutton", "arton", "nitton",  
        "tjugo", "tjugoett", "tjugotvå", "tjugotre", "tjugofyra", "tjugofem", "tjugosex", "tjugosju", "tjugoåtta", "tjugonio",
        "trettio","trettioett", "trettiotvå", "trettiotre", "trettiofyra", "trettiofem", "trettiosex", "trettiosju", "trettioåtta", "trettionio", 
        "fyrtio", "fyrtioett","fyrtiotvå","fyrtiotre","fyrtiofyra","fyrtiofem","fyrtiosex","fyrtiosju","fyrtioåtta","fyrtionio",
        "femtio", "femtioett", "femtiotvå", "femtiotre", "femtiofyra", "femtiofem", "femtiosex", "femtiosju", "femtioåtta", "femtionio",],


      
    }

    
}
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
}
</style>