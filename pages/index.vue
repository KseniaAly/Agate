<script setup>
import FilterComponent from "~/components/ksy/FilterComponent.vue";
import FilterBrand from "~/components/ksy/FilterBrand.vue";
import Car from "~/components/ann/Car.vue";
import FeedBack from "~/components/mp/FeedBack.vue";
</script>

<template>
  <a class="catalog">Каталог коммерческой техники в Нижнем Новгороде</a>
  <div class="page">
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
  margin-left: 75px;
}
.page{
  display: block;
  box-sizing: border-box;
  margin: 0 auto;
  overflow-x: hidden;
  width: 90%;
}
.block{
  display: flex;
}
</style>
