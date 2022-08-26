<template>
  <h1>Vue Reaction Timer Game</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Playground v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Result v-if="showResult" :endTime="score"/>
</template>

<script>
import Playground from './components/Playground.vue';
import Result from './components/Results.vue';
export default {
  name: 'App',
  components: { Playground, Result },
  data(){
    return {
      isPlaying : false,
      showResult: false,
      delay: null,
      score: 0
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
      console.log(this.delay)
    },
    endGame(time){
      this.score = time
      console.log("Timer in Parent",this.score)
      this.showResult = true
      this.isPlaying = false
      this.delay = null
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
  align-items:center;
  color: #444;
  margin-top: 60px;
}
button{
    color: #fff;
    background-color: #28a745;
    border-color: #28a745;
    display: inline-block;
    font-weight: 400;
    text-align: center;
    white-space: nowrap;
    vertical-align: middle;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    border: 1px solid transparent;
    padding: 0.375rem 1.75rem;
    font-size: 1rem;
    line-height: 1.5;
    border-radius: 0.25rem;
    transition: color .15s ease-in-out,background-color .15s ease-in-out,border-color .15s ease-in-out,box-shadow .15s ease-in-out;
}
button:not(:disabled):not(.disabled) {
    cursor: pointer;
}
 button:disabled {
    opacity: .65;
}
</style>
