<template>
    <div id="response">
        <TimerComp/>
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

    #preventive-info {
        background-color: $lightgrey;
        padding: 20px;
    }
</style>