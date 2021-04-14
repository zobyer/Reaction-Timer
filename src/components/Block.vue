<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Block Element
  </div>
</template>

<script>
export default {
    props:['delay'],
    data(){
        return {
            showBlock: false,
            timer: null,
            reactionTime:0,
        }
    },
    mounted(){
        //console.log('block mounted')
        setTimeout(() =>{
            this.showBlock = true
            //console.log(this.delay)
            this.startTimer()
        },this.delay)
    },
    updated(){
        //console.log("value updated")
    },
    unmounted(){
      //console.log("Unmounted")  
    },
    methods:{
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10);
        },
        stopTimer(){
            clearInterval(this.timer)
            //console.log(this.reactionTime)
            this.$emit("send_Time",this.reactionTime)
        }
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