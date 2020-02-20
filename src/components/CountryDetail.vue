<template lang="html">
<main class='detail'>
  <img :src="country.flag" height="200" width="200"/>
  <h3> Name: {{country.name}} </h3>
  <p class='heading'>Capital:</p> <p>{{country.capital}} </p>
  <p class='heading'>Population:</p> <p>{{country.population}} </p>
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
  display: block;
  margin-right: auto;
  margin-left: auto;
  margin-top: 10px;
}

h3 {
  display: flex;
  justify-content: center;
}

p {
  display: flex;
  justify-content: center;
}

ul {
  display: flex;
  justify-content: center;
  padding-left: 10px;
}

li {
  margin-left: 20px;
}
</style>
