<template>
  <div class="container">
    <p v-if="pending">Fetching...</p>
    <pre v-else-if="error">Could not load beers: {{ error.data }}</pre>
    <div class="beers-grid">
      <BeerCard v-for="beer in beers" :beer="beer" />
    </div>
  </div>
</template>


<script setup>
  import BeersCard from "./BeerCard";

  const { data: beers, pending, error } = await useFetch(() => `https://api.punkapi.com/v2/beers?brewed_after=11-2012`)
  console.log(beers);
</script>

<style>
  .beers-grid {
    display: flex;
    width: 100%;
    flex-wrap: wrap;
    gap: 1.5rem
  }
</style>
