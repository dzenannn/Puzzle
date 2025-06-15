<template>
  <PuzzlesComponent @puzzle-changed="onPuzzleChanged" />
  <div v-if="isChosen">
    <RecordsComponent />
  </div>
  <div v-if="isChosen">
    <SliderPuzzle :puzzleId="selectedPuzzleId" />
  </div>
</template>

<script>
import SliderPuzzle from "./components/SliderPuzzle.vue";
import PuzzlesComponent from "./components/Puzzles.vue";
import RecordsComponent from "./components/Records.vue";

export default {
  name: "App",
  components: {
    SliderPuzzle,
    PuzzlesComponent,
    RecordsComponent,
  },
  data() {
    return {
      selectedPuzzleId: null,
      isChosen: false,
    };
  },
  methods: {
    onPuzzleChanged(puzzleId) {
      this.selectedPuzzleId = puzzleId;
      this.isChosen = true;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Arima:wght@100..700&family=Quicksand:wght@300..700&display=swap");
html {
  scroll-behavior: smooth;
}
body {
  min-height: 100vh;
  background: linear-gradient(#3a6073, #3a7bd5);
  font-family: "Quicksand";
  margin-bottom: 10vh;
  text-align: center;
  font-size: 0.75rem;
  color: white;
}

h1,
p,
h2,
h3,
h4,
h5,
h6,
span,
button {
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.75);
}
</style>
