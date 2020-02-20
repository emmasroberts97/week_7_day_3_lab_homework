<template lang="html">
<main>
  <form v-on:submit.prevent="handleSearch">
    <label for="country-search">Search for Countries:</label>
    <input id="country-search" name="country-search" type="search" v-model="selectedCountry"></input>
  </form>
  <div v-if="selectedCountry != null">
  <country-detail v-for="(country, index) in filteredList" :key="index" :country="country" />
</div>
</main>
</template>

<script>
import {eventBus} from '../main.js';
import CountryDetail from './CountryDetail.vue';

export default {
  name: "country-search",
  props: ['countries'],
  data() {
    return {
      selectedCountry: null
    }
  },
  computed: {
    filteredList() {
      return this.countries.filter(country => {
      return country.name.toLowerCase().includes(this.selectedCountry.toLowerCase())
    })
  }
},
  methods: {
    handleSearch() {
      eventBus.$emit('country-search', this.selectedCountry)
    }
  },
  components: {
    'country-detail': CountryDetail
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
