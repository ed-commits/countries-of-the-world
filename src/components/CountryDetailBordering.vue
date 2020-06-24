<template>
  <div v-if="borders">
    <p v-if="borders.length == 0">It is an island!</p>
    <p v-if="borders.length == 1">It is next to {{ borders[0].name }}.</p>
    <p v-if="borders.length > 1">
      It is bordered by
      <ul>
      <li v-for="(border, key) in borders" :key="key" class="item">
        {{ border.name }}
      </li>
      </ul>
    </p>
  </div>
</template>

<script>
function lookupObjectArrayByKey(obArray, key, value) {
  return obArray.find(elt => elt[key] == value);
}

export default {
  name: "CountryDetailBordering",
  data() {
    return { borders: undefined };
  },
  mounted() {
    this.borders = this.country.borders.map(code => {
      return lookupObjectArrayByKey(this.countries, "alpha3Code", code);
    });
  },
  props: ["countries", "country"]
};
</script>

<style>
</style>
