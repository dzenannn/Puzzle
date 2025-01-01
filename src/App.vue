<template>
  <div style="border-bottom: 2px solid black">
    <PuzzlesComponent @puzzle-changed="selectedPuzzleId = $event" />
  </div>
  <div style="border-bottom: 2px solid black; padding-bottom: 1.5rem">
    <RecordsComponent />
  </div>
  <div><SliderPuzzle :puzzleId="selectedPuzzleId" /></div>
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
      selectedPuzzleId: "cut-pink",
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Arima:wght@100..700&family=Quicksand:wght@300..700&display=swap");
html {
  scroll-behavior: smooth;
}
body {
  background: linear-gradient(rgb(69, 94, 0) 70%, rgb(37, 37, 37));
  font-family: "Quicksand";
  margin-bottom: 20vh;
  text-align: center;
  font-size: 0.75rem;
}
</style>
