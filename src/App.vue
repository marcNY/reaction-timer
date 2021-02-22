<template>
  <div>
    <h1>Reaction Timer</h1>
    <Results :score="score" v-if="showResults" />
    <button @click="start" :disabled="isPlaying">play</button>
    <div class="playArea">
      <Block :delay="delay" v-if="isPlaying" @end="endGame"/>
    </div>
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  components: {Block,Results},
  data(){
    return{
      isPlaying: false,
      delay: null,
      score:0,
      showResults:false
    }
  },
  methods:{
  start(){
    this.delay=2000+Math.random()*5000
    this.isPlaying=true
    this.showResults=false
    this.score=0
  },
  endGame(endTime){
    console.log(endTime)
    this.score=endTime
    this.isPlaying=false
    this.showResults=true
  }}
};
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
.playArea {
  border-radius: 25px;
  border: 2px solid #1c1d1b;
  margin: 20px auto;
  padding: 20px;
  width: 50vh;
  height: 50vh;
  position: relative;
}
</style>
