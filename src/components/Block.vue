<template>
  <div class="block" :style="{'top': fromTop, 'left': fromLeft, 'background': getRandomColor()}" v-if="showBlock" @click="stopTimer">
      click me 
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
            fromLeft: this.getRandomNum(80) + '%',
            fromTop: this.getRandomNum(80) + '%',
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        getRandomNum(n) {
            return Math.floor(Math.random() * n)
        },
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        },
        getRandomColor() {
            const r = this.getRandomNum(255)
            const g = this.getRandomNum(255)
            const b = this.getRandomNum(255)
            
            return `rgb(${r}, ${g}, ${b})`
        }
    }
}
</script>

<style>
    .block {
        opacity: 0.7;
        position: absolute;
        width: 200px;
        border-radius: 100px;
        color: black;
        text-align: center;
        padding: 80px 0;
    }
</style>