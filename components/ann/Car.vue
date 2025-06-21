<script>
import CardCar from "~/components/ann/CardCar.vue";

export default {
  components: {
    CardCar
  },
  data() {
    return {
      currentPage: 1, // Текущая страница
      itemsPerPage: 6, // Количество карточек на страницу
      characters: [],  // Данные персонажей
      totalItems: 0,   // Общее количество карточек
    };
  },
  computed: {
    totalPages() {
      return Math.ceil(this.totalItems / this.itemsPerPage);
    },
    displayedItems() {
      const start = (this.currentPage - 1) * this.itemsPerPage;
      const end = start + this.itemsPerPage;
      return this.characters.slice(start, end);
    }
  },
  methods: {
    async fetchData() {
      try {
        const response = await fetch('https://hp-api.onrender.com/api/characters');
        const data = await response.json();
        this.characters = data; // Сохраняем данные в массив
        this.totalItems = this.characters.length; // Обновляем количество товаров
      } catch (error) {
        console.error("Ошибка при получении данных:", error);
      }
    },
    changePage(page) {
      this.currentPage = page;
    }
  },
  created() {
    this.fetchData(); // Загружаем данные при создании компонента
  }
}
</script>

<template>
  <section class="car">
    <div class="container">
      <!-- Генерация карточек товаров, используя данные из API -->
      <card-car v-for="(character, index) in displayedItems" :key="index" :character="character">
        <template #liz>{{ character.name}}</template>
      </card-car>
    </div>

    <!-- Карусель с номерами страниц -->
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
  max-width: 900px;
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

.car {
  display: grid;
  justify-content: center;
}
</style>