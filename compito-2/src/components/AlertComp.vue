<template>
    <div id="alert">
        <div>Stai operando per conto di {{userMail}}</div>
        <a href="#">Torna ad amministrazione</a>
    </div>
</template>

<script>
export default {
  name: 'ResponseComp',
  data() {
    return {

    }
  },
  props: ['userMail'],
}
</script>

<style lang="scss" scoped>
@import '@/assets/styles/palette.scss';

    #alert {
        position: absolute;
        bottom: -35px;
        left: 10px;
        font-size: 12px;
        background-color: $yellorange;
        color: white;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        border-radius: 8px;
        padding: 5px 15px;
    }

    a {
        color: inherit;
    }

    a:hover {
        color: $darkgrey;
    }
</style>