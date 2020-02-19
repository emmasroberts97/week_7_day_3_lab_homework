<template lang="html">
<main>
  <li v-on:click="handleClick">
    {{country.name}}
  </li>
</main>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'country-list-item',
  props: ['country'],
  methods: {
    handleClick() {
      eventBus.$emit('country-selected', this.country)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
