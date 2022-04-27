<template>
<div @click="stopTimer" class="block" v-if="showBlock"><h1>Klicka här!</h1>
<p>{{delay + reactionTime}}</p></div>

  
</template>

<script>
export default {
props: ['delay'],
data(){
    return {
        showBlock: false,
        timer: null,
        reactionTime: 0,
        isReadyForClick: false
    }
},
mounted() {
    
    setTimeout(() => {
        this.showBlock = true
                this.isReadyForClick= true;
    this.$emit('beforeStart', this.isReadyForClick)
    this.startTimer()
    }, this.delay) 
},

methods: {
    startTimer(){
        this.timer = setInterval(() => {
            this.reactionTime += 10;
        }, 10)
    },
    stopTimer(){
        clearInterval(this.timer)
        this.$emit('end', this.reactionTime)
    },
    
}
}
</script>

<style>
    .block{
        max-width: 400px;
        border-radius: 10px;
        background-color: rgb(8, 195, 157);
        color: white;
        text-align: center;
        padding: 15px;
        margin: 20px auto;
    }
</style>