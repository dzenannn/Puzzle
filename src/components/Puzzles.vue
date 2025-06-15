<template>
  <div :style="puzzleClass">
    <h1>Choose a puzzle 👇</h1>
    <div class="map">
      <div class="puzzles">
        <div
          class="puzzle"
          v-for="p of puzzles"
          :key="p.id"
          @click="selectPuzzle(p)"
        >
          <div class="puzzle-img">
            <img id="puzzleImg" :src="require(`../assets/${p.image}`)" />
          </div>
        </div>
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
      puzzleClass: {
        display: "flex",
        flexDirection: "column",
        placeItems: "center",
        fontWeight: "bold",
        textAlign: "center",
      },
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
  /* margin-bottom: 10px; */
  gap: 30px;
}

.puzzle-img {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

#puzzleImg {
  height: 20vh;
  width: 20vw;
}

.puzzle:hover {
  transition: 0.25s;
  scale: 0.98;
}
.puzzle {
  display: grid;
  place-items: center;
  cursor: pointer;
}

.puzzle img:hover {
  transition: 0.25s;
  scale: 1.05;
}

.puzzle img:active {
  transition: 0.25s;
  scale: 0.95;
}

@media (min-width: 550px) {
  .puzzles {
    display: flex;
  }

  .puzzle {
    display: flex;
    width: 20vw;
  }

  .puzzle img {
    border-radius: 15px;
    border: 1px solid black;
    height: 10vh;
    width: 10vw;
  }
}
</style>
