<template>
  <p class="text-center" >Reaction Time : {{ score }} ms</p>
  <p class="rank font-bold">{{rank}}</p>
</template>

<script>
export default {
props:['score'],
data(){
    return{
        rank:null
    }
},
mounted(){
    if(this.score < 250){
        this.rank ="ultra fast"
    }
    else if(this.score < 400){
        this.rank ="fast"
    }
    else{
        this.rank ="snail"
    }
}
}
</script>

<style>

</style>