<template>
  <option :value="index">{{country.name}}</option>
</template>

<script>
import { eventBus } from "../main.js";

export default {
  name: "list-item",
  props: ["country"],
  methods: {
    handleClick() {
      eventBus.$emit("country-selected", this.country);
    }
  }
};
</script>

<style scoped>
</style>