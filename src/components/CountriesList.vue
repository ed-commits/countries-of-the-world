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
      items: [{ name: "Afghanistan" }, { name: "Zimbabwe" }]
    };
  }
};
</script>

<style>
</style>
