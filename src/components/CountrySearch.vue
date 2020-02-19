<template lang="html">
  <form v-on:submit.prevent="handleSearch">
    <input id="country-search" type="search" v-model="selectedCountry"></input>
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
</style>
