<template>
  <div id="app">
    <CountriesList :countries="countries" />
    <CountryDetail :countries="countries" />
    <WorldMapSVG />
  </div>
</template>

<script>
import CountriesList from "./components/CountrySelector.vue";
import CountryDetail from "./components/CountryDetail.vue";
import WorldMapSVG from "./components/WorldMapSVG.vue";

export default {
  name: "App",
  data(){
    return { countries: undefined };
  },
  mounted() {
    fetch("https://restcountries.eu/rest/v2/all")
      .then(res => res.json())
      .then(data => this.countries = data);
  },
  components: {
    CountriesList,
    CountryDetail,
    WorldMapSVG
  }
};
</script>

<style>
#app {
  background-color: whitesmoke;
  font-family: "Alata";
}
</style>
