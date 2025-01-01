<template>
  <div>
    <h1 style="text-align: center; font-weight: bold">
      Izaberite slagalicu 👇
    </h1>
    <div class="row" v-for="p of puzzles" :key="p.id" @click="selectPuzzle(p)">
      <div>
        <img :src="require(`../assets/${p.image}`)" />
      </div>
      <h2>{{ p.title }}</h2>
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
    async selectPuzzle(puzzle) {
      this.$emit("puzzle-changed", puzzle.id);
      setTimeout(() => {
        window.scrollTo({
          top: document.body.scrollHeight,
          behavior: "smooth",
        });
      }, 150);
    },
  },
};
</script>

<style scoped>
.row {
  height: 12.5vh;
  padding: 10px;
  border: 1px solid rgb(0, 0, 0);
  background-color: rgb(206, 206, 206);
  border-radius: 10px;
  display: flex;
  gap: 25px;
  align-items: center;
  max-width: 90vw;
  margin: 10px auto;
  transition: 0.5s;
}

.row:hover {
  scale: 0.98;
}

.row img {
  border-radius: 15px;
  border: 1px solid black;
  height: 10vh;
  width: 25vw;
}
</style>
