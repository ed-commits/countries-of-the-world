<template>
  <div v-if="country">
    <div v-if="country.currencies.length == 1">
      <span
        v-if="country.currencies[0].symbol == null"
      >The currency is {{ country.currencies[0].name }}.</span>
      <span
        v-if="country.currencies[0].symbol != null"
      >The currency is {{ country.currencies[0].name }} ({{ country.currencies[0].symbol }}).</span>
    </div>
    <div v-if="country.currencies.length > 1">
      The country uses the following currencies:
      <ul>
        <li v-for="(currency, key) in country.currencies" :key="key">
          <span v-if="currency.symbol == null">The {{ currency.name }}.</span>
          <span
            v-if="currency.symbol != null"
          >The {{ currency.name }} ({{ currency.symbol }}).</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "CountryDetailCurrencies",
  props: ["country"]
};
</script>

<style>
</style>
