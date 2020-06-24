<template lang="html">
  <option :value="country.alpha3Code">{{ country.name }}</option>
</template>

<script>
export default {
  name: "CountrySelectorItem",
  props: ["country"]
};
</script>

<style>
</style>
