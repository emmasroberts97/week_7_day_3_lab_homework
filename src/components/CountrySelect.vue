<template lang="html">
  <select v-on:change="handleChange" v-model="selectedCountry">
    <option value="" disabled selected>Choose a Country</option>
    <option v-for="(country, index) in countries" :key="index" :value="country"> {{country.name}} </option>
  </select>

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
</style>
