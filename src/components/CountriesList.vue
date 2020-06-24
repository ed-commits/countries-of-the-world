<template>
  <div>
    This is the countries list.
    <ul>
      <li v-for="(item, index) in items" :key="index" :item="item">{{ item.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "countries-list",
  data() {
    return {
      items: []
    };
  },
  mounted() {
    fetch("https://restcountries.eu/rest/v2/all")
      .then(res => res.json())
      .then(data => (this.items = data));
  }
};
</script>

<style>
</style>
