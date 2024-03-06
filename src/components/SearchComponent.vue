<template>
  <div class="search-container container mt-5">
    <label for="search">Select Year</label>
    <select
      id="search"
      class="form-control"
      :v-model="year"
      @change="$emit('selectChange', $event.target.value)"
    >
      <option value="All">All</option>
      <option
        v-for="(item, index) in populations"
        :key="index + '-OPTION'"
        :value="item.Year"
      >
        {{ item.Year }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "SearchComponent",
  props: ["populations", "year"],
};
</script>

<style>
.search-container {
  position: relative;
  max-width: 500px !important;
}

.search-container label {
  position: absolute;
  top: -10px;
  left: 30px;
  background-color: white;
  padding: 0 20px;
  font-size: 12px;
}

.search-container select {
  height: 45px !important;
}
</style>
