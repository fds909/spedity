<template>
  <div id="app">
    <HeaderComp :userMail="userMail" />
    <MainComp :order="order"/>
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
      order: {
        // imponibile
        taxable: 125.0,
        vat: 0,
        total: 0
      }
    }
  },
  mounted() {
    this.calculateTotal();
  },
  methods: {
    calculateTotal() {
      const VAT_RATE = 22;

      this.order.vat = this.order.taxable * VAT_RATE / 100;
      this.order.total = this.order.taxable + this.order.vat;
    }
  }
}
</script>

<style lang="scss">

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    font-size: 14px;
  }

</style>
