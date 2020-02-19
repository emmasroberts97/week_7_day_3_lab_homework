<template lang="html">
<main>
  <h1>Countries of the World</h1>
  <!-- <countries-list :countries='countries' /> -->
  <country-select :countries='countries' />
  <country-detail :country="selectedCountry" v-if="selectedCountry"/>
</main>
</template>

<script>
import CountriesList from './components/CountriesList.vue'
import CountryDetail from './components/CountryDetail.vue'
import CountrySelect from './components/CountrySelect.vue'
import { eventBus } from './main.js'


export default {
  name: 'app',
  data() {
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(result => result.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    })
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail,
    "country-select": CountrySelect
  }
}
</script>

<style lang="css" scoped>
</style>
