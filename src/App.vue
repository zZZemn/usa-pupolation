<template>
  <div id="app">
    <SearchComponent
      :populations="populations.data"
      :year="yearSelected"
      @selectChange="changeSelect"
    />
    <PopulationsContainer
      :populations="populations.data"
      :year="yearSelected"
    />
  </div>
</template>

<script>
import PopulationsContainer from "./components/PopulationsContainer.vue";
import SearchComponent from "./components/SearchComponent.vue";

export default {
  name: "App",
  data: function () {
    return {
      url: "https://datausa.io/api/data?drilldowns=Nation&measures=Population",
      populations: [],
      yearSelected: "All",
    };
  },
  components: {
    PopulationsContainer,
    SearchComponent,
  },
  methods: {
    changeSelect: function (selected) {
      this.yearSelected = selected;
    },
  },
  mounted: function () {
    fetch(this.url)
      .then((response) => response.json())
      .then((data) => {
        this.populations = data;
        console.log(this.populations);
      });
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
