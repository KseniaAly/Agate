<script setup>
import FilterComponent from "~/components/ksy/FilterComponent.vue";
import FilterBrand from "~/components/ksy/FilterBrand.vue";
import Car from "~/components/ann/Car.vue";
import FeedBack from "~/components/mp/FeedBack.vue";
</script>

<template>
  <div class="page">
    <a class="catalog">Каталог коммерческой техники в Нижнем Новгороде</a>
    <filter-brand class="right"/>
    <div class="block">
      <filter-component/>
      <car></car>
      <filter-brand class="left"/>
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
.right{
  display: none;
}

@media (max-width: 768px) {
  .right{
    display: flex;
    margin-bottom: 30px;
  }
  .left{
    display: none;
  }
  .catalog{
    font-size: 18px;
  }
  .page{
    max-width: 720px;
  }
}
@media (max-width: 480px) {
  .right{
    display: none;
  }
  .page{
    max-width: 90%;
  }
}
</style>
