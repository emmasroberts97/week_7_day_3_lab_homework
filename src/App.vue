<template lang="html">
<main>
  <h1>Countries of the World</h1>
  <country-search />
  <!-- <countries-list :countries='countries' /> -->
  <country-select :countries='countries' />
  <country-detail :country="selectedCountry" v-if="selectedCountry"/>
</main>
</template>

<script>
import CountriesList from './components/CountriesList.vue'
import CountryDetail from './components/CountryDetail.vue'
import CountrySelect from './components/CountrySelect.vue'
import CountrySearch from './components/CountrySearch.vue'
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
    eventBus.$on('country-search', (location) => {
      for (let country of this.countries) {
        if (country.name == location){
          this.selectedCountry = country;
        }
        }
      })
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail,
    "country-select": CountrySelect,
    "country-search": CountrySearch
  }
}
</script>

<style lang="css" scoped>
main {
background-image: url('../public/antique-map.jpeg');
background-size: cover;
}
</style>
