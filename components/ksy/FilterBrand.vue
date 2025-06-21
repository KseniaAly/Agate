<script setup>
import BrandComponent from "~/components/ksy/BrandComponent.vue";

import {ref} from "vue";

const brands = ref([
  {name: 'Камаз', src: "/img/Kamaz.svg"},
  {name: 'Хино', src: '/img/Hino.svg'},
  {name: 'МАЗ', src: '/img/Maz.svg'},
  {name: 'Тракс', src: '/img/DaewoTracks.svg'},
  {name: 'Шакман', src: '/img/Shackman.svg'},
  {name: 'Гром', src: '/img/Grom.svg'}
])
</script>

<template>
  <div class="body">
  <brand-component v-for="(brand) in brands" :img="brand"/>
  </div>
</template>

<style scoped>
*{
  display: block;
  font-family: Monserrat;
}
  .body{
    padding: 20px 17px;
    border: 4px solid #880003;
    border-radius: 5px;
    width: fit-content;
    height: fit-content;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-bottom: 0;
    position: relative;
  }
</style>