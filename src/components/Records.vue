<template>
  <div>
    <h1>Records</h1>
    <button :style="buttonStyle" @click="getRecords">Refresh Button</button>
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
      buttonStyle: {
        backgroundColor: "#3a7bd5",
        color: "white",
        border: "1px solid #fff",
        padding: "10px 20px",
        borderRadius: "5px",
        cursor: "pointer",
      },
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
