<template>
  <div class="container text-center mt-5">
    <h2 class="text-info mt-5">USA Population Data</h2>
    <div
      class="population-main-container mt-5 d-flex justify-content-between flex-wrap m-auto"
    >
      <div
        class="population-container card mt-2 p-3 text-center"
        v-for="(item, index) in filteredPopulations"
        :key="index"
      >
        <h4 class="text-secondary">{{ item.Year }}</h4>
        <h6 class="text-secondary">{{ formatPopulation(item.Population) }}</h6>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PupulationsContainer",
  props: ["populations", "year"],
  computed: {
    filteredPopulations() {
      if (this.year === "All") {
        return this.populations;
      } else {
        return this.populations.filter((item) => item.Year == this.year);
      }
    },
  },
  methods: {
    formatPopulation(population) {
      return Number(population).toLocaleString();
    },
  },
};
</script>

<style scoped>
.population-main-container {
  max-width: 1000px;
}

.population-main-container .population-container {
  width: 300px;
}
</style>
