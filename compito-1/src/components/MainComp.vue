<template>
    <main>
        <div class="ms_container">
            <PreventiveInfo :prevInfo="prevInfo"/>

            <ResponseComp :contactPhone="contactPhone"/>
        </div>
    </main>
</template>

<script>
import PreventiveInfo from './PreventiveInfo.vue'
import ResponseComp from './ResponseComp.vue'

export default {
  name: 'MainComp',
  components: {
    PreventiveInfo,
    ResponseComp
  },
  data() {
    return {

    }
  },
  props: ['contactPhone', 'prevInfo'],
}
</script>

<style lang="scss">
@import '@/assets/styles/palette.scss';

main {
    margin: 50px 0;
}

.ms_container {
    width: 75%;
    margin: auto;
}

</style>