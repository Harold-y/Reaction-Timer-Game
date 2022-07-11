<template>
    <p>Reaction Time: {{ reactionTime }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['reactionTime'],
    data () {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.reactionTime < 250) {
            this.rank = "Awesome!"
        }else if (this.reactionTime < 400)
        {
            this.rank = 'Rapid Move!'
        }else {
            this.rank = 'Snail Pace...'
        }
    }
}
</script>

<style>
.rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
}
</style>