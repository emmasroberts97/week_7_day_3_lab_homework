<template lang="html">
<main>
  <img :src="country.flag" height="200" width="200"/>
  <h3> Name: {{country.name}} </h3>
  <p> <p class='heading'>Capital:</p> {{country.capital}} </p>
  <p> <p class='heading'>Population:</p> {{country.population}} </p>
  <p class='heading'> Languages: </p>
  <ul>
    <li v-for="(language, index) in country.languages" :key="index" :value="language">{{language.name}}</li>
  </ul>
</main>

</template>

<script>
export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
p.heading{
  font-weight: bold;
}
img{
  margin-top: 10px;
}
</style>
