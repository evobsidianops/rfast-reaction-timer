<template>
    <div class="block" @click="stopTimer" v-if="showBlock">
        click me
    </div>
</template>

<script>
export default {
    props: ["delay"],
    data() {
        return {
            timer: null,
            reactionTime: 0,
            showBlock: false
        }
    },
    mounted() {
        setTimeout(() => {
            console.log("component Mounted")
        this.showBlock = true
        this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit("end", this.reactionTime)
            console.log(this.reactionTime)
        }
    }
   
}

</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>