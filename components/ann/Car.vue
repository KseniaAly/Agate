<script>
import CardCar from "~/components/ann/CardCar.vue";

export default {
  components: {
    CardCar
  },
  data() {
    return {
      currentPage: 1,
      itemsPerPage: 6,
      cars: [],
      totalItems: 0,
    };
  },
  computed: {
    totalPages() {
      return Math.ceil(this.totalItems / this.itemsPerPage);
    },
    displayedItems() {
      const start = (this.currentPage - 1) * this.itemsPerPage;
      const end = start + this.itemsPerPage;
      return this.cars.slice(start, end);
    }
  },
  methods: {
    async fetchData() {
      try {
        const response = await fetch('https://hp-api.onrender.com/api/characters');
        const data = await response.json();
        this.cars = data;
        this.totalItems = this.cars.length;
      } catch (error) {
        console.error("Ошибка при получении данных:", error);
      }
    },
    changePage(page) {
      this.currentPage = page;
    }
  },
  created() {
    this.fetchData();
  }
}
</script>

<template>
  <section class="car">
    <div class="container">
      <card-car v-for="(car, index) in displayedItems" :key="index" :car="car">
        <template #h3>{{car.name}}</template>
        <template #img><img :src="car.image" alt=""></template>
        <template #left>
          {{car.gender}} <br>
          {{car.species}} <br>
          {{car.gender}} <br>
          {{car.species}}
        </template>
        <template #liz>{{car.house}}</template>
        <template #hoz>{{car.house}}</template>
      </card-car>
    </div>


    <div class="carousel-nav">
      <button
          v-for="page in totalPages"
          :key="page"
          class="carousel-btn"
          @click="changePage(page)"
          :class="{'active': page === currentPage}"
      >
        {{ page }}
      </button>
    </div>
  </section>
</template>

<style scoped>
.container {
  display: flex;

  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
}

.carousel-nav {
  margin-top: 20px;
  text-align: center;
}

.carousel-btn {
  margin: 0 5px;
  padding: 5px 10px;
  background: #ddd;
  border: none;
  cursor: pointer;
}
img{
  height: 170px;
  width: 100%;
  border-radius: 10px 10px 0 0;
  object-fit: cover;
}
.carousel-btn.active {
  background: #880003;
  color: #fff;
}

.car {
  display: grid;
  justify-content: center;
}
</style>