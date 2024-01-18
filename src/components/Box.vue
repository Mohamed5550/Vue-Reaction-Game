<template>
    <div class="box" @click="stopTimer" v-if="isStarted">Click me</div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            isStarted: 0,
            timer: null,
            reactionTime: 0
        }
    },
    methods: {
        stopTimer() {
            clearInterval(this.timer);
            this.$emit("end", this.reactionTime);
        },
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10)
        }
    },
    mounted() {
        setTimeout(() => {
            this.isStarted = 1;
            this.startTimer();
        }, this.delay)
    },
}
</script>

<style scoped>
    .box {
        width: 400px;
        border-radius: 20px;
        text-align: center;
        padding: 100px 0;
        background: #0faf87;
        margin: 40px auto;
        color: #FFF;
        font-size: 20px
    }
</style>