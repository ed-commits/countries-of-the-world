<template>
  <div><div v-if="country" class="detail-box">
      <img class="flagImage" :src="country.flag" />
      The country is {{ country.name }} and has a population of {{ country.population }}. It's capital is {{country.capital}}.
      </div></div>
</template>

<script>
import { eventBus } from "../main.js";

console.log(eventBus);

export default {
  name: "CountryDetail",
  data(){
      return {
          country: undefined
      }
  },
  mounted(){
      eventBus.$on('CountrySelected', (newCountry) => {
          this.country = newCountry
      })
  }
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


</style>
