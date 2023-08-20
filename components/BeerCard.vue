<template>
  <article class="beer-card">
    <div class="beer-card__header">
      <img :src="beer.image_url" :alt="beer.name"  />
      <hgroup>
        <h5>{{ beer.name }}</h5>
        <small>{{ beer.description }}</small>
      </hgroup>
    </div>
    <img v-if="beer.lactose"
         class="beer-card__lactose"
         :src="lactose"
         alt="Contains Lactose"
    />
    <div v-if="beer.dryHopped" class="beer-card__hopped">
      DRY<br>HOPPED
    </div>
    <BeerRibbon :name="beer.tagline.substring(0, 30)" />
    <div class="beer-card__more-details">
      <BeerDetails :beer="beer" />
    </div>
  </article>
</template>

<script setup>
import lactose from 'assets/images/lactose.png';
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

      img {
        height: 280px;
      }

      small {
        font-size: 0.675rem;
        overflow: hidden;
        display: -webkit-box;
        -webkit-line-clamp: 5;
        -webkit-box-orient: vertical;
      }
    }

    &__lactose {
      height: 2rem;
      position: absolute;
      top: 0.5rem;
      left: 0.5rem;
    }

    &__hopped {
      position: absolute;
      color: #007500;
      top: 0.5rem;
      left: 0.5rem;
      font-size: 0.5rem;
      padding: 0.5rem 0.25rem;
      border: 1px solid;
      text-align: center;
      line-height: 10px;
      border-radius: 50%;
      font-weight: 900;

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
