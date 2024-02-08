<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isplaying" id="startbtn">play</button>
  <block  v-if="isplaying" :Delay="Delay" @end="endgame" />
  <result v-if="showresult"  :score="score" />
</template>

<script>
import block from './components/block.vue'
import result from './components/result.vue'

export default {
  name: 'App',
  components: { block, result },
  data(){
    return {
      isplaying: false,
      Delay: null,
      score: null,
      showresult: false
    }
  },
  methods: {
    start(){
      this.Delay = 2000 + Math.random() * 5000
      this.isplaying = true
      this.showresult = false
      // console.log(this.delay);
    },
    endgame(reactiontime){
      this.score = reactiontime
      this.isplaying = false
      this.showresult = true
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
#startbtn{
  border: none;
  padding: 8px;
  border-radius: 5px;
  background: #0faf87;
  color: white;
  cursor: pointer;
  width: 100px;
}
#startbtn[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
