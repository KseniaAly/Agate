<script setup>
import ModalWindow from "~/components/ksy/ModalWindow.vue";
import FilterComponent from "~/components/ksy/FilterComponent.vue";
import FilterBrand from "~/components/ksy/FilterBrand.vue";
import Car from "~/components/ann/Car.vue";
import FeedBack from "~/components/mp/FeedBack.vue";
</script>

<template>
  <a class="catalog">Каталог коммерческой техники в Нижнем Новгороде</a>
  <div class="page" style="display: flex">
      <filter-component/>
      <car></car>
      <filter-brand/>
    </div>
  <feed-back/>
</template>

<style scoped>
.catalog{
  font-size: 24px;
}
</style>
