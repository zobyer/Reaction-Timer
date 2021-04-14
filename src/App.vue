<template>
<h1>Welcome to Reaction Timer</h1>
<button @click="Start" :disabled="isPlaying">Click</button>
<Block v-if="isPlaying" :delay="delay" @send_Time="save_Time" />
<Result v-if="show_result" :result="click_Time"/>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Results.vue'


export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return{
      isPlaying : false,
      delay:null,
      click_Time: null,
      show_result: null
    }
  },
  methods:{
    Start(){
      this.delay = 2000 + Math.random()*5000
      this.isPlaying = true
      //console.log(this.delay)
      this.show_result = false
    },
    save_Time(time) {
      //console.log(time)
      this.click_Time = time
      this.isPlaying = false
      this.show_result = true
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
</style>
