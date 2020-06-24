<template>
  <div>
    <select v-model="countryCode" v-on:change="changed">
      <CountrySelectorItem v-for="(item, key) in countries" :key="key" :country="item" />
    </select>
  </div>
</template>

<script>
import CountrySelectorItem from "./CountrySelectorItem.vue";
import { eventBus } from "../main.js";
import { worldMapBus } from "../main.js";

function lookupObjectArrayByKey(obArray, key, value) {
  return obArray.find(elt => elt[key] == value);
}

export default {
  name: "CountrySelector",
  data() {
    return {
      countryCode: undefined
    };
  },
  computed: {
    country() {
      return lookupObjectArrayByKey(this.countries, "alpha3Code", this.countryCode);
    }
  },
  methods: {
    changed() {
      eventBus.$emit("CountrySelected", this.country);
      worldMapBus.$emit("CountrySelected", this.country);
    }
  },
  props: ['countries'],
  components: {
    CountrySelectorItem: CountrySelectorItem
  },
};
</script>

<style>
</style>
