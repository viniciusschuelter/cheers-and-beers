<template>
  <div class="container">
    <div class="beers-grid">
      <BeerCard v-for="beer in beers" :beer="beer" />
    </div>
  </div>
</template>


<script setup>
  let beers = await $fetch('https://api.punkapi.com/v2/beers?brewed_after=11-2012');

  beers = checkLactoseAndHops(beers);
  beers = removeCentennial(beers);
  beers = orderByAbv(beers);

  function removeCentennial(items) {
    return items.filter( _ => !_.ingredients?.hops?.some( __ => __.name.includes('Centennial')));
  }

  function orderByAbv(items) {
    return items.sort( (a, b) => a.abv - b.abv);
  }

  function checkLactoseAndHops(items) {
    return items.map( _ => ({
        ..._,
        lactose: _.method?.twist?.includes('lactose'),
        dryHopped: _.method?.twist?.includes('dry hops')
    }));
  }
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
