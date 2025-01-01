<template>
  <div style="border-bottom: 2px solid black">
    <PuzzlesComponent @puzzle-changed="onPuzzleChanged" />
  </div>
  <div
    v-if="isChosen"
    style="border-bottom: 2px solid black; padding-bottom: 1.5rem"
  >
    <RecordsComponent />
  </div>
  <div v-if="isChosen"><SliderPuzzle :puzzleId="selectedPuzzleId" /></div>
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
  background: linear-gradient(40deg, #b3b3b3 30%, #0c8ea5) no-repeat;
  font-family: "Quicksand";
  margin-bottom: 10vh;
  text-align: center;
  font-size: 0.75rem;
}
</style>
