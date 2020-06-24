<template>
  <div><div v-if="country">This is the country detail.</div></div>
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
</style>
