<template>
  <div>
    This is the countries list.
    <ul>
      <ListComponent v-for="(item, index) in items" :key="index" :country="item"></ListComponent>
    </ul>
  </div>
</template>

<script>
import ListComponent from "./ListComponent.vue";

export default {
  name: "CountriesList",
  data() {
    return {
      items: []
    };
  },
  mounted() {
    fetch("https://restcountries.eu/rest/v2/all")
      .then(res => res.json())
      .then(data => (this.items = data));
  },
  components: {
    'ListComponent': ListComponent
  }
};
</script>

<style>
</style>
