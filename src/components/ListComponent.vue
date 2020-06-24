<template lang="html">
  <li v-on:click="handleClick">{{country.name}}</li>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'ListComponent',
    props: ['key', 'country'],
    methods: {
        handleClick(){
            eventBus.$emit('CountrySelected', this.country)
        }
    }
}
</script>

<style>

</style>
