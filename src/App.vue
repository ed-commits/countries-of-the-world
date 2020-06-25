<template>
  <div id="app">
    <h1>Countries of the World!</h1>
    <div class="card">
    <CountriesList :countries="countries" />
    <CountryDetail :countries="countries" />
    </div>
    <div class="card">
    <WorldMapSVG />
    </div>
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
body {
  background-color: whitesmoke;
}

#app {
  font-family: "Alata";
}

h1 {
  text-align: center;
}

.card {
  padding: 20px;
  width: 80%;
  max-width: 960px;
  margin: 0 auto;
  box-shadow: 0 .5em 2em rgba(0,0,0,0.3);
  margin-bottom: 3em;
}

</style>
