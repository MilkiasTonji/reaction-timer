<template>
    <div class="result">
        <p>The reaction time: {{ score }} ms </p>
        <p>Your rank: {{ rank }} </p>
    </div>
</template>

<script>
export default {
    props:['score'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if(this.score < 250){
            this.rank = 'Ninja Fingers'
        }else if(this.score < 400){
            this.rank = 'Rapid reflexes'
        }else{
            this.rank = 'snail paces. You are too slow'
        }
    }
}
</script>

<style>
    .result{
        text-align: center;
        color: #444;
        margin-top: 60px;
        border: #444 1px solid;
        padding: 50px;
        width: 400px;
        margin-left: 400px;
    }
    
</style>