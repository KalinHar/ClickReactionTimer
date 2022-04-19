<template>
  <div class="block" :style="{'top': fromTop, 'left': fromLeft}" v-if="showBlock" @click="stopTimer">
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
            fromLeft: Math.floor(Math.random() * 80) + '%',
            fromTop: Math.floor(Math.random() * 80) + '%',
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
    .block {
        position: absolute;
        width: 200px;
        border-radius: 20px;
        background: rgb(18, 84, 84);
        color: white;
        text-align: center;
        padding: 80px 0;
        /* margin: 40px; */
    }
</style>