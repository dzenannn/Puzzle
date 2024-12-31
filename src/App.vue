<template>
  <PuzzlesComponent @puzzle-changed="selectedPuzzleId = $event" />
  <RecordsComponent />
  <SliderPuzzle :puzzleId="selectedPuzzleId" />
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
body {
  min-height: 140vh;
}
</style>
