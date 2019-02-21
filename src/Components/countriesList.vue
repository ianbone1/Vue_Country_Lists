<template>
  <div>
    <label class="selectLabel" for="countrySelector">Select Country</label>
    <select id="countrySelecter" v-model="countryIndex" v-on:change="selectHandler">
      <!-- <list-item v-for="(country, index) in countries" :country="country" :key="index"></list-item> -->
      <option v-for="(country, index) in countries" :value="index">{{country.name}}</option>
    </select>
    <!-- countryIndex= {{countryIndex}} -->
  </div>
</template>

<script>
// import ListItem from './ListItem.vue'
import { eventBus } from "../main.js";

export default {
  name: "countries-list",
  data() {
    return {
      countryIndex: null
    };
  },
  props: ["countries"],
  components: {
    // "list-item": ListItem
  },
  methods: {
    selectHandler() {
      eventBus.$emit("country-selected", this.countries[this.countryIndex]);
    }
  }
};
</script>

<style scoped>
</style>