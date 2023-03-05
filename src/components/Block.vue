<template>
  <div
    class="block bg-green-400 rounded text-center px-100 mx-40 my-auto"
    v-if="showBlock" @click="stopTimer"
  >
    click me
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer:null,
      reactionTime:0
    }
  },
  mounted() {
    console.log("component mounted");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer()
    }, this.delay);
  },
  methods: {
    startTimer(){
        this.timer = setInterval(() =>{
            this.reactionTime += 10
        }, 10)
    },
    stopTimer(){
        clearInterval(this.timer)
        this.$emit('end', this.reactionTime)
    }
  }
//   updated() {
//     console.log('component updated')
//   },
//   unmounted(){
//     console.log('Component unmounted')
//   }
};
</script>

<style>
</style>