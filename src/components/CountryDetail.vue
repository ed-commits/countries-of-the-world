<template>
  <div>
    <div v-if="country" class="detail-box">
      <div class="flagBox">
        <img class="flagImage" :src="country.flag" />
      </div>
      <h2>
        {{ country.name }} (
        <i>{{ country.nativeName }}</i>)
      </h2>
      <p>The capital of {{ country.name }} is {{ country.capital }}.</p>
      <p>
        The {{ country.demonym }} people make up a
        population of {{ country.population }} in a region of size {{ country.area }} km
        <sup>2</sup>.
      </p>
      <CountryDetailLanguages :country="country"/>
      <CountryDetailCurrencies :country="country"/>
      <CountryDetailBordering :countries="countries" :country="country"/>
    </div>
  </div>
</template>

<script>
import CountryDetailLanguages from "./CountryDetailLanguages.vue";
import CountryDetailCurrencies from "./CountryDetailCurrencies.vue";
import CountryDetailBordering from "./CountryDetailBordering.vue";
import { eventBus } from "../main.js";

export default {
  name: "CountryDetail",
  data() {
    return {
      country: undefined
    };
  },
  mounted() {
    eventBus.$on("CountrySelected", newCountry => {
      this.country = newCountry;
    });
  },
  components: {
    CountryDetailLanguages: CountryDetailLanguages,
    CountryDetailCurrencies: CountryDetailCurrencies,
    CountryDetailBordering: CountryDetailBordering
  },
  props: ['countries']
};
</script>

<style>
.detail-box {
  background-color: white;
  border: 2px solid black;
  width: 60ch;
  padding: 12px;
}

img.flagImage {
  float: right;
  width: 200px;
  margin: 20px;
  border: 1px solid black;
}

.clearfix::after {
  content: "";
  clear: both;
  display: table;
}

div.country {
  background-color: white;
  border: 2px solid black;
  width: 60ch;
  padding: 12px;
}

img.flagImage {
  float: right;
  width: 200px;
  margin: 20px;
  border: 1px solid black;
}
</style>
