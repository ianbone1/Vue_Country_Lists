
<template lang="html">
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <countries-list :countries="countries"></countries-list>
      <country-details :country="selectedCountry"></country-details>
    </div>
  </div>
</template>

<script>
import CountriesList from "./Components/countriesList.vue";

import { eventBus } from "./main.js";
import countryDetails from "./Components/countryDetails.vue";

export default {
  data() {
    name: "app";
    return {
      countries: [],
      selectedCountry: null
    };
  },
  components: {
    "countries-list": CountriesList,
    "country-details": countryDetails
  },
  mounted() {
    fetch("https://restcountries.eu/rest/v2/all")
      .then(res => res.json())
      .then(countries => (this.countries = countries));
    eventBus.$on("country-selected", country => {
      this.selectedCountry = country;
    });
  }
};
</script>

<style lang="css" scoped>
.main-container {
  display: flex;
  justify-content: space-between;
}
</style>
