<template>
    <div id="response" class="border rounded my-2 py-3 d-flex flex-column align-items-center">
      <p class="mb-5">Appena riceverai i preventivi te li mostreremo qui. Inoltre li riceverai via email.</p>
      <TimerComp class="mb-3"/>
      <p class="text-center">Abbiamo inviato la tua richiesta ai nostri trasportatori <br/>
        La maggior parte delle offerte viene inviata entro 60 minuti nei giorni lavorativi</p>

      <p class="text-center"> In caso di dubbi chiamaci al 
        <span class="label-green rounded-pill py-2">
          <img class="headphone-icon mx-1" src="@/assets/icons/headset.svg" alt="Headset Icon">
          <span>+39 06 56548263</span>
        </span>
      </p>
    </div>
</template>

<script>
import TimerComp from './TimerComp.vue'

export default {
  name: 'ResponseComp',
  components: {
    TimerComp
  },
  data() {
    return {

    }
  },
  props: [],
}
</script>

<style lang="scss" scoped>
@import '@/assets/styles/palette.scss';

    #response {
        font-size: 14px;
    }

    .headphone-icon {
      height: 20px;
      width: 20px;
      filter: invert(100%);
    }
</style>