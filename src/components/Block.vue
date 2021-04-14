<template>
  <div class="block" v-if="showBlock">
      Block Element
  </div>
</template>

<script>
import { onUpdated } from 'vue'
export default {
    props:['delay'],
    data(){
        return {
            showBlock: false
        }
    },
    mounted(){
        console.log('block mounted')
        setTimeout(() =>{
            this.showBlock = true
            console.log(this.delay)
        },this.delay)
    },
    updated(){
        console.log("value updated")
    },
    unmounted(){
      console.log("Unmounted")  
    }
}
</script>

<style>
.block{
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>