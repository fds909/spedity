<template>
    <main>
        <div class="ms_container">
            <PreventiveInfo/>
            <ResponseComp/>
        </div>
    </main>
</template>

<script>
import PreventiveInfo from './PreventiveInfo.vue'

export default {
  name: 'MainComp',
  components: {
    PreventiveInfo
  },
  data() {
    return {

    }
  },
  props: [],
}
</script>

<style lang="scss">
@import '@/assets/styles/palette.scss';

main {
    margin: 50px 0;
}

.ms_container {
    width: 90%;
    margin: auto;
}

</style>