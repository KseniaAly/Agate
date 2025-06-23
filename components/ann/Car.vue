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
    },
    displayedPageNumbers() {
      const maxVisiblePages = 10;
      const startPage = Math.floor((this.currentPage - 1) / maxVisiblePages) * maxVisiblePages + 1;
      const endPage = Math.min(startPage + maxVisiblePages - 1, this.totalPages);

      return Array.from({ length: endPage - startPage + 1 }, (_, i) => startPage + i);
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
      if (page >= 1 && page <= this.totalPages) {
        this.currentPage = page;
      }
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
        event.stopPropagation();
      }
    },
    closeWindow() {
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
      >
        <template #h3>{{ car.name }}</template>
        <template #img><img :src="car.image" alt=""></template>
        <template #left>
          {{ car.gender }} <br>
          {{ car.species }} <br>
        </template>
        <template #liz>{{ car.house }}</template>
        <template #hoz>{{ car.house }}</template>
        <template #button>
          <button @click.stop="window_open = true">Узнать цену</button>
        </template>
      </card-car>
    </div>

    <div class="carousel-nav">
      <button
          @click="changePage(currentPage - 1)"
          :disabled="currentPage <= 1"
          class="carousel-btn"
      >
        Назад
      </button>

      <button
          v-for="page in displayedPageNumbers"
          :key="page"
          class="carousel-btn"
          @click="changePage(page)"
          :class="{'active': page === currentPage}"
      >
        {{ page }}
      </button>

      <button
          @click="changePage(currentPage + 1)"
          :disabled="currentPage >= totalPages"
          class="carousel-btn"
      >
        Вперёд
      </button>
    </div>

    <modal-car
        :isVisible="isModalVisible"
        :carSelect="selectedCar"
        @close="closeModal"
    />

    <modal-window :open="window_open" @close="closeWindow" />
  </section>
</template>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
}
.container button{
  transition: 0.3s;
}
.container button:hover{
  cursor: pointer;
  background-color: #9a3c3c;
  transition: 0.3s;
}
.carousel-nav {
  margin-top: 20px;
  text-align: center;
}

.carousel-btn {
  margin: 0 5px;
  padding: 5px 10px;
  background: #ffffff;
  border: 1px solid #880003;
  cursor: pointer;
  margin-bottom: 10px;
  border-radius: 5px;
}
.carousel-btn:hover{
  background: #DADADA;
}
.carousel-btn.active {
  background: #880003;
  color: #fff;
}

.carousel-btn:disabled {
  background: #ccc;
  cursor: not-allowed;
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

.container button {
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
