<template lang="html">
<div>
  <!-- <ul>
    <country-list-item v-for="(country, index) in countries" :key="index" :country="country" />
  </ul> -->

</div>
</template>

<script>
import CountryListItem from './CountryListItem.vue';
import CountrySelect from './CountrySelect.vue';

export default {
  name: 'countries-list',
  props: ['countries'],
  components: {
    "country-list-item": CountryListItem,
    "country-select": CountrySelect
  }
}
</script>

<style lang="css" scoped>
</style>
