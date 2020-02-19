<template lang="html">
  <form v-on:submit.prevent="handleSearch">
    <label for="country-search">Search for Countries:</label>
    <input id="country-search" name="country-search" type="search" v-model="selectedCountry" autocomplete="country"></input>
  </form>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: "country-search",
  data() {
    return {
      selectedCountry: []
    }
  },
  methods: {
    handleSearch() {
      eventBus.$emit('country-search', this.selectedCountry)
    }
  }
}
</script>

<style lang="css" scoped>
input {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}

label {
  display: flex;
  justify-content: center;
}
</style>
