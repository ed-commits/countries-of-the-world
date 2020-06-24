<template>
  <div v-if="country">
    <div
      v-if="country.languages.length == 1"
    >The spoken language is {{ country.languages[0].name }}.</div>
    <div v-if="country.languages.length > 1">
      <p>The languages spoken are:</p>
      <ul>
        <li v-for="(language, key) in country.languages" :key="key">
          {{ language.name }}
          <i>({{ language.nativeName }})</i>.
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "CountryDetailLanguage",
  props: ["country"]
};
</script>

<style>
</style>
