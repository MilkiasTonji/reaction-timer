<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Click me 
  </div>
</template>

<script>

export default {
    props: ['delay'],
    data(){
        return{
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    methods:{
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime += 10
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    },
    mounted(){
        // this is the place where we fetch the request
        setTimeout(()=>{
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    // updated(){
    //     console.log("Component updated....")
    // },
    // unmounted(){
    //     // this is used in vue at routing, moving from one component to another
    //     // oftenly used for the vue router
    //     console.log('Component unmounted or removed')
    // }

}

</script>

<style>
    .block{
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0px;
        margin: 40px auto;
    }
</style>