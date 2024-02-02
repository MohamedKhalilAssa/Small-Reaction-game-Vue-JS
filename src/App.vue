<template>
  <h1>Hello! let's test those reflexes!! </h1>
  <button @click="start" :disabled="showBox"  class="btn btn-dark mt-5">Play the game</button>
  <br>
  <Block  :shown="showBox" :delay="delay" v-if="showBox" @end="stopGame" />
  <Result v-if="showResult" :reactionTime="reactionTime" />
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Block,Result
  },
  methods:{
      start(){
        this.showBox = true
        this.showResult = false
        this.delay = 2000 + Math.random() * 4000
      },
      stopGame(reactionTime){
        this.reactionTime = reactionTime
        this.showBox = false
        this.showResult = true
      }
  },
  data(){
    return {
      showBox: false,
      delay:0,
      reactionTime:0,
      showResult:false
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
  min-height:50vh;
}
</style>
