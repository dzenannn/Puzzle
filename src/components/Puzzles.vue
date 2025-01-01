<template>
  <div>
    <h1 style="text-align: center; font-weight: bold">
      Izaberite slagalicu 👇
    </h1>
    <div class="row" v-for="p of puzzles" :key="p.id">
      <div>
        <img :src="require(`../assets/${p.image}`)" />
      </div>
      <h2>{{ p.title }}</h2>
      <div class="play-button">
        <button @click="selectPuzzle(p)">Izaberi</button>
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
        { id: "cut-pink", image: "pink.jpg", title: "Roze Cvet" },
        { id: "cut-red", image: "red.jpg", title: "Crveni Cvet" },
        { id: "cut-purple", image: "purple.jpg", title: "Ljubičasti Cvet" },
        { id: "cut-glavonja", image: "glavonja.jpg", title: "Glavonja" },
        { id: "cut-cs", image: "cs.jpg", title: "Kanter Strajk" },
      ],
    };
  },
  methods: {
    selectPuzzle(puzzle) {
      this.$emit("puzzle-changed", puzzle.id);
      window.scrollTo({
        top: document.body.scrollHeight,
        behavior: "smooth",
      });
    },
  },
};
</script>

<style scoped>
.row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 100vw;
  margin: auto;
}

.row img {
  width: 30vw;
}
</style>
