<template>
  <p>Reaction time - {{ score }} ms.</p>
  <p class="rank">Rank: {{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null,
        }
    },
    mounted() {
        if (this.score < 150) {
            this.rank = 'Flash'
        }else if (this.score < 250) {
            this.rank = 'Ninja'
        }else if (this.score < 450) {
            this.rank = 'Normal'
        }else {
            this.rank = 'Snail ...'
        }
    }
}
</script>

<style>
    .rank {
        font-size: 1.4rem;
        color: blue;
        font-weight: bold;
    }
</style>