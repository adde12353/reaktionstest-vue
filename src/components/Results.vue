<template>
    <p class="rank">{{rank}}</p>
  <p>Reaktionstid : {{ score }}ms</p>
  
</template>

<script>
export default {
props : ['score'],

data(){
    return {
        rank:null
    }
},
mounted(){
    if(this.score < 250){
        this.rank = "Ninja Fingrar"
    } else if (this.score < 400) {
        this.rank = "Snabba Fingrar"
    } else {
        this.rank = 'Kom igen nu! Snabbare kan du'
    }
}
}
</script>

<style>
.rank{
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
}
</style>