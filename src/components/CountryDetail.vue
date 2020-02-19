<template lang="html">
<main>
  <h3> {{country.name}} </h3>
  <p> {{country.capital}} </p>
  <p> {{country.population}} </p>
  <img :src="country.flag" height=200 width=200/>
</main>

</template>

<script>
export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
</style>
