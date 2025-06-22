<script>
import CardCar from "~/components/ann/CardCar.vue";
import ModalCar from "~/components/ann/ModalCar.vue";
import ModalWindow from "~/components/ksy/ModalWindow.vue";

export default {
  components: {
    ModalWindow,
    CardCar,
    ModalCar
  },
  data() {
    return {
      currentPage: 1,
      itemsPerPage: 6,
      cars: [],
      totalItems: 0,
      isModalVisible: false,
      selectedCar: null,
      window_open: false,
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
    },
    openModal(car) {
      this.selectedCar = car;
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
      this.selectedCar = null;
    },
    preventModal(event) {
      if (event.target.tagName === "BUTTON") {
        event.stopPropagation();  // Предотвращаем открытие модалки
      }
    },
    closeWindow(){
      this.window_open = false;
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
      <card-car
          v-for="(car, index) in displayedItems"
          :key="index"
          :car="car"
          @click="openModal(car)"
          @click.stop="preventModal">
      <template #h3>{{ car.name }}</template>
      <template #img><img :src="car.image" alt=""></template>
      <template #left>
        {{ car.gender }} <br>
        {{ car.species }} <br>
      </template>
      <template #liz>{{ car.house }}</template>
      <template #hoz>{{ car.house }}</template>
      <template #button>
        <button @click.stop @click="this.window_open=true">Узнать цену</button>
      </template>
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


    <modal-car
        :isVisible="isModalVisible"
        :carSelect="selectedCar"
        @close="closeModal">
    </modal-car>
  </section>
  <modal-window :open="window_open" @closeWindow="closeWindow"/>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');
*{
  margin: 0;
  padding: 0;
  font-family: 'Montserrat';
}
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

.carousel-btn.active {
  background: #880003;
  color: #fff;
}

img {
  height: 170px;
  width: 100%;
  border-radius: 10px 10px 0 0;
  object-fit: cover;
}

.car {
  display: grid;
  justify-content: center;
}
.container button{
  background: #880003;
  color: #fff;
  align-self: end;
  width: 90%;
  padding: 10px;
  border-radius: 10px;
  border: none;
  font-size: 1rem;
  font-weight: 600;
}

</style>
