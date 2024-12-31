<template>
  <div>
    <h1>Select a Puzzle</h1>
    <div class="row" v-for="p of puzzles" :key="p.id">
      <div>
        <img :src="require(`../assets/${p.image}`)" />
      </div>
      <div>
        <h2>{{ p.title }}</h2>
      </div>
      <div class="play-button">
        <button @click="selectPuzzle(p)">Play</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PuzzlesComponent",
  data() {
    return {
      puzzles: [
        { id: "cut-pink", image: "pink.jpg", title: "Pink Flower" },
        { id: "cut-red", image: "red.jpg", title: "Red Flower" },
      ],
    };
  },
  methods: {
    selectPuzzle(puzzle) {
      this.$emit("puzzle-changed", puzzle.id);
    },
  },
};
</script>

<style scoped>
.row {
  display: flex;
  max-width: 90vw;
  gap: 2.25rem;
}

.row img {
  width: 100px;
}

.row .play-button {
  padding-top: 25px;
}
</style>
