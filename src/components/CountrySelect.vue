<template lang="html">
<main>
  <select v-on:change="handleChange" v-model="selectedCountry">
    <option value="" disabled selected>Choose a Country</option>
    <option v-for="(country, index) in countries" :key="index" :value="country"> {{country.name}} </option>
  </select>
</main>

</template>

<script>

import {eventBus} from '../main.js'

export default {
  name: "country-select",
  data() {
    return {
    selectedCountry: []
   }
  },
  props: ['countries'],
  methods: {
    handleChange() {
      eventBus.$emit('country-selected', this.selectedCountry)
    }
  }
}
</script>

<style lang="css" scoped>
select{
  display: block;
  margin-left: auto;
  margin-right:auto;
  margin-top: 10px;
}
</style>
