<template>
    <div class="progress-steps">
        <div class="progress"></div>
        <div class="progress-bg"></div>
        <div class="circle"></div>
        <div class="circle"></div>
        <div class="circle"></div>
        <div class="circle"></div>
    </div>
</template>

<script>

export default {
  name: 'ProgressStepsComp',
  data() {
    return {
        circles: [],
        progress: null
    }
  },
  props: ['currentActive'],
  mounted() {
    this.circles = document.querySelectorAll('.circle');
    this.progress = document.querySelector('.progress');

    this.update();
  },
  methods: {
    update() {
        console.log('test');

        this.circles.forEach((circle, index) => {
            if (index <= this.currentActive) {
                circle.classList.add('visited');
                if (index === this.currentActive) {
                    circle.classList.add('active');
                }
            } else {
                circle.classList.remove('active');
            }

            const visited = document.querySelectorAll('.visited');

            this.progress.style.width = ((visited.length -1)/ (this.circles.length - 1)) * 100 + '%';
        });
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/styles/palette.scss';

.progress-steps {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 500px;
    margin-bottom: 50px;
    position: relative;
}

.circle {
    height: 25px;
    width: 25px;
    background-color: $midgrey;
    border: 3px solid $midgrey;
    border-radius: 50%;
}

.circle.visited {
    border-color: $green;
}

.circle.visited.active {
    background-color: $green;
}

.progress-items::before {
    content: '';
    background-color: $midgrey;
    position:  absolute;
    top: 50%;
    left: 0;
    transform: translateY(-50%);
    height: 3px;
    width: 100%;
    z-index: -1;
}

.progress-bg {
    background-color: $midgrey;
    position:  absolute;
    top: 50%;
    left: 0;
    transform: translateY(-50%);
    height: 3px;
    width: 100%;
    z-index: -2;
    transition: width 0.5s ease;
}

.progress {
    background-color: $green;
    position:  absolute;
    top: 50%;
    left: 0;
    transform: translateY(-50%);
    height: 3px;
    width: 0%;
    z-index: -1;
    transition: width 0.5s ease;
}
</style>