<script setup>
import FilterComponent from "~/components/ksy/FilterComponent.vue";
import FilterBrand from "~/components/ksy/FilterBrand.vue";
import Car from "~/components/ann/Car.vue";
import FeedBack from "~/components/mp/FeedBack.vue";
</script>

<template>
  <div class="page">
    <a class="catalog">Каталог коммерческой техники в Нижнем Новгороде</a>
    <div class="block">
      <filter-component/>
      <car></car>
      <filter-brand/>
    </div>
  </div>
  <feed-back/>
</template>

<style scoped>
.catalog{
  font-size: 24px;
  margin-top: 20px;
  display: block;
  margin-bottom: 20px;
}
.page{
  display: block;
  box-sizing: border-box;
  margin: 0 auto;
  overflow-x: hidden;
  max-width: 1330px;
}
.block{
  display: flex;
}
</style>
