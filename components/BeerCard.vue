<template>
  <article class="beer-card">
    <img :src="beer.image_url" :alt="beer.name"  />
    <hgroup>
      <h5>{{ beer.name }}</h5>
      <div>{{ beer.description }}</div>
    </hgroup>
    <div class="beer-card__more-details">
      <div>
        Ibu: <span>{{ beer.ibu }}</span>
      </div>
      <div>
        Abv: <span>{{ beer.abv }}</span>
      </div>
    </div>
  </article>
</template>

<script setup>
const props = defineProps(['beer'])
</script>


<style lang="scss">
  .beer-card {
    display: flex;
    align-items: center;
    flex-direction: column;
    position: relative;
    width: 320px;
    height: 480px;
    transition: ease-in-out .2s;


    &:hover {
      scale: 1.1;
      align-items: baseline;


      .beer-card__more-details {
        visibility: initial;
      }
    }

    img {
      height: 280px;
    }

    .beer-card__more-details {
      position: absolute;
      visibility: hidden;
      display: flex;
      flex-direction: column;
      width: 50%;
      right: 0;
      transition: ease-in-out .2s;
      font-size: 14px;
    }
  }
</style>
