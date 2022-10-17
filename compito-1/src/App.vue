<template>
  <div id="app">
    <HeaderComp :userMail="userMail"/>
    <MainComp :contactPhone="contactPhone" :prevInfo="prevInfo"/>
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue'

export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  data() {
    return {
      userMail: 'info@spedity.com',
      contactPhone: '+39 06 56548263',
      prevInfo: {
            shippingId: 'ffc78c0b',
            priority: 'Standard',
            message: '',
            content: 'Merce generica',
            value: 300,
            pallet: {
                weight: 100,
                height: 100,
                length: 100,
                width: 100,
                quantity: 1
            },
            shippingDate: '14/10/2022',
            departurePlace: {
                city: 'Sora',
                cap: '03039',
                province: 'FR'
            },
            deliveryPlace: {
                city: 'Vivaro Romano',
                cap: '00020',
                province: 'RM'
            },
            expirDate: '24/10/2022',
            expirTime: '0:00',
            vehicleEquip: 'Sponda Idraulica  Alza/Abbassa',
            extraServ: ''
        }
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/styles/palette.scss';

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    font-size: 14px;
  }

  // Buttons
  .btn {
    font-size: 14px !important;
  }

  .btn-primary {
    background-color: $blue !important;
    color: white;
  }

  .btn-secondary {
    color: black !important;
    background-color: $midgrey !important;
    border: 0 !important;
  }

  .btn-active {
    outline: $blue solid 1px;
  }

  .label-green {
    color: white;
    background-color: $green;
    padding: 5px 10px;
  }
</style>
