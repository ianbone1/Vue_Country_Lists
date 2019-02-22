<template>
  <div>
    <label class="selectLabel" for="countrySelector">Select Country</label>
    <select id="countrySelecter" v-model="countryIndex" v-on:change="selectHandler">
      <option v-for="(country, index) in countries" :value="index">{{country.name}}</option>
    </select>

    <div class="input_box">
      <label for="input_box">Search Country</label>
      <input type="text" placeholder="Filter Countries...." id="input_box" value="" v-model="input_box"  v-on:keyup="filterCountries">
    </input>
  </div>

  <div class="filterList" v-if="checkEmpty">
    <list-item  v-for="(country, index) in countriesFiltered" :country="country" :key="index"></list-item>
  </div>

</div>
</template>

<script>
import ListItem from './ListItem.vue';
import { eventBus } from "../main.js";

export default {
  name: 'countries-list',
  data() {
    return {
      countryIndex: null,
      input_box:  "",
      countriesFiltered: []
    };
  },
  props: ['countries'],
  components: {
    "list-item": ListItem
  },
  computed: {
    checkEmpty() {
      if (this.countries.length==0) {
        return false;
      }
      if (this.countriesFiltered.length == 0){
        this.countriesFiltered = this.countries;
      }
      return true;
    }
  },
  methods: {
    selectHandler() {
      eventBus.$emit("country-selected", this.countries[this.countryIndex]);
    },
    filterCountries() {
      if (this.countries) {
        this.countriesFiltered=this.countries;
        this.countriesFiltered=this.countriesFiltered.filter((c,i) => c.name.toLowerCase().includes(this.input_box.toLowerCase()));
      } else {
        this.countriesFiltered=[];
      }
    }
  }
};
</script>

<style scoped>
.filterList{
  padding-top: 20px;
}

</style>
