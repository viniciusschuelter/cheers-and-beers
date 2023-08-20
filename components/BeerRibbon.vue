<template>
  <div class="ribbon ribbon-top-right">
    <span>{{ name }}</span>
  </div>
</template>


<script setup>
const props = defineProps(['name'])
</script>

<style lang="scss">

/* common */
.ribbon {
  width: 200px;
  height: 200px;
  overflow: hidden;
  position: absolute;
  z-index: 2;

  ::before,
  ::after {
    position: absolute;
    z-index: -1;
    content: '';
    display: block;
    border: 5px solid #2980b9;
    transform: rotate(-45deg);
  }

  span {
    position: absolute;
    display: block;
    width: 240px;
    padding: 8px 16px 8px 0;
    background-color: #3498db;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
    color: #fff;
    font-size: 0.5rem;
    font-weight: 600;
    text-shadow: 0 1px 1px rgba(0, 0, 0, 0.2);
    text-transform: uppercase;
    text-align: center;
  }
}

/* top right*/
.ribbon-top-right {
  top: -10px;
  right: -10px;

  ::before,
  ::after {
    border-top-color: transparent;
    border-right-color: transparent;
  }
  ::before {
    top: 26px;
    left: 6px;
  }
  ::after {
    bottom: -5px;
    right: 5px;
  }

  span {
    left: 8px;
    top: 56px;
    transform: rotate(45deg);
  }
}
</style>
