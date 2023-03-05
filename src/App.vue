// <script setup>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
// </script>

<template>
  <header>
    <!-- <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" /> -->

    <div class="wrapper">
      <!-- <HelloWorld msg="You did it!" /> -->
      <h3 class="text-center font-bold">DON Reaction Timer</h3>
    </div>
  </header>

  <main class="text-center">
    <!-- <TheWelcome /> -->
    <button
      class="bg-blue-200 px-2 rounded"
      @click="start"
      :disabled="isPlaying"
    >
      play
    </button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Results v-if="showResults" :score="score" />
  </main>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults:false,
    };
  },
  methods: {
    start() {
      //min of 2s and max of 7s
      // this.delay = 2000 + Math.random() + 5000
      this.delay = Math.floor(Math.random() * (7000 - 2000 + 1)) + 2000;
      this.isPlaying = true;
      this.showResults=false
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults=true;
    },
  },
};
</script>


<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
