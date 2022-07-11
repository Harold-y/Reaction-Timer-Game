<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
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
            reactionTime: 0
        }
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {this.reactionTime += 10}, 10) // run every 10ms
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('endTimer', this.reactionTime)
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    updated() {
        // any update on data etc. will trigger this hook
        console.log('component updated!')
    },
    unmounted() {
        // once the component is destroied, this will be triggered
        console.log('unmounted!')
    }
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background:  #0faf87;;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>