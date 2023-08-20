<template>
  <article class="beer-card">
    <BeerRibbon :name="beer.tagline.substring(0, 30)" />
    <div class="beer-card__header">
      <img :src="beer.image_url" :alt="beer.name"  />
      <hgroup>
        <h5>{{ beer.name }}</h5>
        <small>{{ beer.description }}</small>
      </hgroup>
    </div>
    <div class="beer-card__more-details">
      <BeerDetails :beer="beer" />
    </div>
  </article>
</template>

<script setup>
const props = defineProps(['beer'])
</script>


<style lang="scss">
  .beer-card {
    position: relative;
    width: 320px;
    height: 480px;
    transition: ease-in-out .2s;
    padding: 1.5rem;
    margin: 0;

    &__header {
      display: flex;
      align-items: center;
      flex-direction: column;
      font-size: 0.75rem;

      h5 {
        font-size: 0.875rem;
        margin-top: 0.75rem;
      }

      small {
        font-size: 0.675rem;
        overflow: hidden;
        display: -webkit-box;
        -webkit-line-clamp: 5;
        -webkit-box-orient: vertical;
      }
    }


    &:hover {
      scale: 1.05;

      .beer-card__more-details {
        display: flex;
      }

      .beer-card__header {
        align-items: baseline;

        hgroup {
          filter: blur(1.3px);
        }
      }

    }

    img {
      height: 280px;
    }

    &__more-details {
      position: absolute;
      display: none;
      flex-direction: column;
      width: 60%;
      height: 100%;
      background: #00000080;
      right: 0;
      top: 0;
      font-size: 14px;
      overflow: hidden;
      border-top-right-radius: 5px;
      border-bottom-right-radius: 5px;
      -webkit-animation: fadein 2s; /* Safari, Chrome and Opera > 12.1 */
      animation: fadein 0.5s;
    }
  }

  @keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
  }

</style>
