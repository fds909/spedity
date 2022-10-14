<template>
  <div id="app">
    <HeaderComp :userMail="userMail"/>
    <MainComp/>
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

    }
  }
}
</script>

<style lang="scss">
@import '@/assets/styles/palette.scss';

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
</style>
