<template>
  <h1>Catch me if you can...</h1>
  <button @click="start" :disabled="isPlayed">Play</button>
  <div v-if="isPlayed">
    <Block :displayTime="displayTime" @endGame="endGame" />
  </div>
 
  <!-- <p >Result : {{score}} ms</p> -->
  <div v-if="end">
    <Result :score="score"/>
  </div>
</template>

<script>
import Block from "./components/Block.vue"
import Result from "./components/Result.vue"

export default {
  
  name: 'App',
  components: {
    Block,
    Result
  },
  data(){
    return{
      isPlayed: false,
      displayTime: null,
      score: 0,
      end: false,
    }
  },
  methods: {
    start(){
      this.isPlayed = true;
      // console.log(3000+Math.random()*5000);
      this.displayTime = 1000+Math.random()*5000;
    },
    endGame(score){
      // console.log(score);
      this.score = score;
      this.isPlayed = false;
      this.end = true;
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
