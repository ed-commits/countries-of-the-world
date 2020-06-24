<template>
  <div id="app">
    <CountryDetail />
    <CountriesList />
  </div>
</template>

<script>
import CountriesList from "./components/CountriesList.vue";
import CountryDetail from "./components/CountryDetail.vue";

export default {
  name: "App",
  components: {
    CountriesList,
    CountryDetail
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
