<template>
<div class="bg" @click.self="clickAndFake">
<h1>Reaktion med Vue.js</h1>
<button id="start-btn" @click="startA" :disabled="isPlaying">Starta spelet</button>
<Block v-if="isPlaying" :delay="delay" @end="endGame" @beforeStart="isReadyForClick"/>
<Results v-if="showResults" :score="score" />
</div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results }, 
    data() {
return {
   isPlaying: false,
   delay: null,
   score: null,
   showResults: false,
   beforeWIndoe: false
 }
 }, 
  methods: {
    startA() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true;
      this.showResults = false
    },
  endGame(reactionTime) {
    this.score = reactionTime;
    this.isPlaying = false
    this.showResults = true
  },
  isReadyForClick(event){
    this.beforeWIndoe = event
  },
  clickAndFake(){
if(!this.beforeWIndoe) {
  alert("Vänta på att klicka på innan den gröna rutan kommer fram")
}
  }
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

.bg{
  height: 80vh;
}

#start-btn{
  margin-top: 30%;
  font-size: 1.6em;
  border-radius: 0.2em;
  padding: 2px 10px;
}
</style>
