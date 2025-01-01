<template>
  <div>
    <h1>Rekordi 🏆</h1>
    <button @click="getRecords">Osveži 🔁</button>
    <div v-for="(r, index) of records" :key="index">
      {{ index + 1 }} - {{ r.elapsedTime }}
    </div>
  </div>
</template>

<script>
export default {
  name: "RecordsComponent",
  data() {
    return {
      records: [],
    };
  },
  created() {
    this.getRecords();
  },
  methods: {
    getRecords() {
      const records = JSON.parse(localStorage.getItem("records")) || [];
      this.records = records;
    },
  },
};
</script>
