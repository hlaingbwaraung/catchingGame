<template>
  <h1>How fast can u catch me?</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <div v-if="isPlaying">
     <Block :delay="delay" @endGame="endGame"/>
  </div>
 <p>Result is {{score}}</p>
</template>

<script>
import Block from "./components/Block.vue"


export default {
  name:'App',
  components:{
    Block
  },
data(){
      return{
        isPlaying:false,
        delay:null
      }
  },
  methods:{
    start(){
        this.isPlaying=true,
        this.delay=2000+Math.random()*5000;
    },
      endGame(score){
    console.log(score)
  }
  },

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