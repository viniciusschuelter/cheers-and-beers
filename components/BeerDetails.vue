<template>
  <div class="beer-details">
    <label>Ibu:
      <span>{{ beer.ibu }}</span>
    </label>
    <label>Abv:
      <span>{{ beer.abv }}</span>
    </label>
    <label>Ebc:
      <span>{{ beer.ebc || 'none' }}</span>
    </label>
    <label>Ph:
      <span>{{ beer.ph }}</span>
    </label>
    <label>Attenuation:
      <span>{{ beer.attenuation_level }}</span>
    </label>
    <label>Food pairing:
      <span v-for="food in beer.food_pairing">{{ food }}; </span>
    </label>
  </div>
</template>

<script setup>
  const props = defineProps(['beer'])
</script>

<style lang="scss">
  .beer-details {
    padding: 1rem 0.5rem;
    color: #fff;

    label {
      font-weight: 700;
      font-size: 14px;

      span {
        font-weight: 400;
        font-size: 0.675rem;
      }
    }
  }
</style>
