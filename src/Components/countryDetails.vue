<template>
    <div v-if="country">
        <h1>
            {{country.name}}
        </h1>
        <ul>
            <li>Capital: {{country.capital}}</li>
            <li>Population: {{country.population}}</li>
            
        </ul>

    </div>
</template>

<script>
    export default {
        name: "country-detail",
        props: ["country"]
        
    }
</script>

<style scoped>

</style>