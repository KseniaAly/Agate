<script setup>
import BrandComponent from "~/components/ksy/BrandComponent.vue";

import {ref} from "vue";

const brands = ref([
  {name: 'Газ', src: '/img/GAZ.png', link: '&brand_name=ГАЗ'},
  {name: 'Камаз', src: "/img/Kamaz.svg", link: '8'},
  {name: 'Хино', src: '/img/Hino.svg', link: '8'},
  {name: 'МАЗ', src: '/img/Maz.svg', link: '8'},
  {name: 'Тракс', src: '/img/DaewoTracks.svg', link: '8'},
  {name: 'Шакман', src: '/img/Shackman.svg', link: '8'}
])

const emit = defineEmits(['update'])
function updateLink(newLink){
  emit('update', newLink)
}
</script>

<template>
  <div class="body">
    <brand-component v-for="(brand) in brands" :img="brand" class="brand" @update="updateLink"/>
  </div>
</template>

<style scoped>
*{
  display: block;
  font-family: Monserrat;
}
  .body{
    padding: 20px 17px;
    border: 3px solid #880003;
    border-radius: 5px;
    width: fit-content;
    height: fit-content;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-bottom: 0;
    position: relative;
  }

  .brand:nth-child(1) :deep(img){
    width: 130px;
  }

@media (max-width: 768px) {
  .body{
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    width: 100%;
  }
  .brand:nth-child(1) :deep(img){
    width: 80px;
  }
}
</style>