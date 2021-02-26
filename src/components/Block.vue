<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
        }   
    },
    mounted() {
        console.log('mount')
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            console.log(this.delay)
        }, this.delay)
    },
    updated() {
        console.log('components updated')
    },
    unmounted() {
        console.log('unmounted') 
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            this.timer = 0 
            console.log(this.reactionTime)
            console.log(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
    .block{
        width: 400px;
        border-radius: 20px;
        background-color: rgb(0, 158, 105);
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>