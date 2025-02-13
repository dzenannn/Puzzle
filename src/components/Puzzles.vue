<template>
  <!-- test -->
  <div>
    <h1 style="text-align: center; font-weight: bold">
      Izaberite slagalicu 👇
    </h1>
    <div class="puzzles">
      <div
        class="row"
        v-for="p of puzzles"
        :key="p.id"
        @click="selectPuzzle(p)"
      >
        <div>
          <img :src="require(`../assets/${p.image}`)" />
        </div>
        <h2>{{ p.title }}</h2>
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
      }, 200);
    },
  },
};
</script>

<style scoped>
.puzzles {
  flex-wrap: wrap;
  justify-content: center;
  margin-bottom: 10px;
  gap: 20px;
}

.row {
  height: 11vh;
  padding: 10px;
  border: 1px solid rgb(0, 0, 0);
  background-color: rgb(206, 206, 206);
  border-radius: 10px;
  display: flex;
  gap: 10px;
  align-items: center;
  max-width: 90vw;
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

@media (min-width: 550px) {
  .puzzles {
    display: flex;
  }

  .row {
    display: flex;
    width: 20vw;
  }

  .row img {
    border-radius: 15px;
    border: 1px solid black;
    height: 10vh;
    width: 10vw;
  }
}
</style>
