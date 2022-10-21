<template>
    <div id="timer">
        <!-- Hours -->
        <div class="time-frame" id="hours">
          <div class="value">{{currentHour}}</div>
          <div class="desc">Ore</div>
        </div>

        <!-- Minutes -->
        <div class="time-frame" id="minutes">
          <div class="value">{{currentMin}}</div>
          <div class="desc">Minuti</div>
        </div>

        <!-- Seconds -->
        <div class="time-frame" id="seconds">
          <div class="value">{{currentSec}}</div>
          <div class="desc">Secondi</div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'TimerComp',
  data() {
    return {
      // i minuti in input al componente vengono convertiti in secondi
      secondsLeft: parseInt(this.mins) * 60,
      currentSec: '00',
      currentMin: '00',
      currentHour: '00'
    }
  },
  props: [ 'mins' ],
  mounted() {
    this.countdown();
  },
  methods: {
    countdown() {
      let timer = setInterval(() => {
      this.secondsLeft--;
      this.updateTimer();
      if (this.secondsLeft === 0) {
        clearInterval(timer);
      }
      }, 1000);
    },
    updateTimer() {
      this.currentSec = this.secondsLeft % 60;
      this.currentSec = this.keep2Digits(this.currentSec);

      this.currentMin = Math.floor(this.secondsLeft / 60) % 60;
      this.currentMin = this.keep2Digits(this.currentMin);

      this.currentHour = Math.floor(this.secondsLeft / 60 / 60);
      this.currentHour = this.keep2Digits(this.currentHour);
    },
    // mantiene il valore nel formato a due cifre con '0' in prima posizione (es 00, 01)
    keep2Digits(value) {
      return (value < 10) ? '0' + value : value;
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/styles/palette.scss';

  #timer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 25vw;
    min-width: 245px;
    color: white;
  }

  .time-frame {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 80px;
    width: 80px;
    background-color: black;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 3px 3px 5px #cacaca;
  }

  .time-frame .value {
    font-size: 35px;
  }
  .time-frame .desc {
    font-size: 15px;
  }

</style>