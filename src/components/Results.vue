<template>
  <p>Reaction Time: {{ this.scoresss }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['scoresss'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.scoresss < 250) {
            this.rank = 'Ninja Fingers'
        } else if (this.scoresss < 400) {
            this.rank = 'Rapid Reflexes'
        } else {
            this.rank = 'Snail Pace...'
        }
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: red;
        font-weight: bold;
    }
</style>