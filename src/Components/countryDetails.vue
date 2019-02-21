<template>
  <div v-if="country">
    <h1>{{country.name}}</h1>
    <ul>
      <li>Capital: {{country.capital}}</li>
      <li>Population: {{country.population}}</li>
      <li>Country Flag:</li>
      <li>
        <img :src="country.flag" width="200px" height="200px">
      </li>
      <li>Languages:</li>
      <li v-for="(language, index) in country.languages">{{language.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "country-detail",
  props: ["country"]
};
</script>

<style scoped>
</style>