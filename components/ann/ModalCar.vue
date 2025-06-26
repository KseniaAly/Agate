<script setup>
import { ref } from 'vue';

const showMore = ref(false);

defineProps({
  isVisible: {
    type: Boolean,
    required: true
  },
  carSelect: {
    type: Object,
    required: true
  }
});
defineEmits(["close"]);
</script>


<template>
  <div v-if="isVisible" class="modal-overlay" @click="$emit('close')">
    <div class="modal-content" @click.stop>
      <div class="card">
        <img :src="carSelect.model.image || 'https://agat-technic.ru/upload/files/7661930/a3d16153aaa1d500b9cc2af9efa87b24.png'" alt="Product Image">
        <div class="card-content">
          <h2>{{ carSelect.name }}</h2>
          <div class="flex">
            <div class="grid">
              <h3>Технические характеристики</h3>
              <div class="flex2"><p>Тип двигателя</p><p>{{ carSelect.properties.engine_type }}</p></div>
              <div class="flex2"><p>Трансмиссия</p><p>{{ carSelect.properties.transmission }}</p></div>
              <div class="flex2"><p>Тип кузова</p><p>{{ carSelect.properties.body_type }}</p></div>
              <div class="flex2"><p>Год выпуска</p><p>{{ carSelect.properties.year_of_manufacture }}</p></div>
            </div>
            <div class="grid">
              <div class="right">
                <p class="price">{{ carSelect.price.toLocaleString('ru-RU') }}₽</p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <transition name="fade-slide">
      <div v-if="showMore" class="card-bottom">
        <div class="flex-wrap">
        <div class="grid">
          <h3>Двигатель</h3>
          <div class="flex2"><p>Тип двигателя</p><p>{{ carSelect.properties.engine_type }}</p></div>
          <div class="flex2"><p>Крутящий момент</p><p>{{ carSelect.properties.turning_torque }}</p></div>
          <div class="flex2"><p>Объем двигателя</p><p>{{ carSelect.properties.engine_volume }}</p></div>
          <div class="flex2"><p>Расположение цилиндров</p><p>{{ carSelect.properties.cylinder_configuration }}</p></div>
          <div class="flex2"><p>Мощность двигателя л.с. при об/мин</p><p>{{ carSelect.properties.engine_power }}</p></div>
          <div class="flex2"><p>Экологический класс</p><p>{{ carSelect.properties.environmental_class.toUpperCase() }}</p></div>
        </div>

          <div class="grid">
            <h3>Трансмиссия</h3>
            <div class="flex2"><p>Трансмиссия</p><p>{{ carSelect.properties.transmission }}</p></div>
            <div class="flex2"><p>Тип привода</p><p>{{ carSelect.properties.gear_type }}</p></div>
            <div class="flex2"><p>Число передач</p><p>{{ carSelect.properties.gear_number }}</p></div>
          </div>

          <div class="grid">
            <h3>Габариты</h3>
            <div class="flex2"><p>Длина, мм</p><p>{{ carSelect.properties.length }}</p></div>
            <div class="flex2"><p>Ширина, мм</p><p>{{ carSelect.properties.width }}</p></div>
            <div class="flex2"><p>Высота, мм</p><p>{{ carSelect.properties.height }}</p></div>
            <div class="flex2"><p>Диаметр разворота, м</p><p>{{ carSelect.properties.turn_diameter }}</p></div>
          </div>

          <div class="grid">
            <h3>Подвеска</h3>
            <div class="flex2"><p>Колея передняя, мм</p><p>{{ carSelect.properties.front_track }}</p></div>
            <div class="flex2"><p>Колея задняя, мм</p><p>{{ carSelect.properties.back_track }}</p></div>
            <div class="flex2"><p>Колесная база, мм</p><p>{{ carSelect.properties.wheel_base }}</p></div>
          </div>

          <div class="grid">
            <h3>Динамические характеристики</h3>
            <div class="flex2"><p>Максимальная скорость, км/ч</p><p>{{ carSelect.properties.max_speed }}</p></div>
          </div>

          <div class="grid">
            <h3>Общие</h3>
            <div class="flex2"><p>Тип кузова</p><p>{{ carSelect.properties.body_type }}</p></div>
          </div>
          <div class="grid">
            <h3>Масса</h3>
            <div class="flex2"><p>Снаряженная масса, кг</p><p>{{ carSelect.properties.unladen_weight }}</p></div>
            <div class="flex2"><p>Полная масса, кг</p><p>{{ carSelect.properties.gross_weight }}</p></div>
          </div>

          <div class="grid">
            <h3>Размеры</h3>
            <div class="flex2"><p>Количество мест</p><p>{{ carSelect.properties.seats }}</p></div>
          </div>
        </div>
      </div>
      </transition>
      <button class="card-button" @click="showMore = !showMore">
        {{ showMore ? 'Скрыть больше характеристик' : 'Показать больше характеристик' }}
      </button>
    </div>
  </div>
</template>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;

}

.modal-content {
  background: #fff;
  padding: 20px 50px 20px 50px;
  width: 80%;
  height: 90%;
  overflow-y: auto;
  border: #880003 solid 4px;
  border-radius: 10px;
}

.card {
  border-radius: 10px;
  width: 100%;
  display: flex;
  align-items: start;
}

.card-content {
  display: grid;
  justify-items: center;
  padding: 10px;
  align-content: space-between;
}

h3 {
  font-size: 1.2rem;
  font-weight: 500;
  text-align: center;
}
h2{
  text-align: center;
}

.grid {
  display: grid;
  font-size: 1rem;
  margin-top: 10px;
  align-content: start;
}

.flex {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 100%;
  margin-top: 10px;
}

.right img {
  height: 30px;
  width: 40px;
}

.right {
  display: flex;
  align-items: center;
}

img {
  width: 50%;
  object-fit: cover;
  border-radius: 10px 10px 0 0;
}

.flex2{
  display: flex;
  width: 90%;
  justify-content: space-between;
  margin-top: 10px;
}
.flex2 p:nth-child(2){
  color: #5c5c5c;
}
.card-bottom .flex2{
  background: #efefef;
  padding: 5px 10px 5px 10px;
  border-radius: 5px;
}
.card-bottom .grid{
  width: 50%;
  justify-items: center;
}
.price{
  font-size: 1.4rem;
  font-weight: 600;
}
.flex-wrap{
  display: flex;
  flex-wrap: wrap;
}
.card-button{
  margin-left: 25px;
  margin-top: 15px;
  font-size: 1.2rem;
  background: none;
  border: none;
  cursor: pointer;
  color: #880003;
  font-weight: 500;
}

.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.4s ease;
}
.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

@media (max-width: 980px) {
  .card{
    display: grid;
  }
  img{
    width: 100%;
  }
}

@media (max-width: 768px) {
  .flex-wrap{
    display: grid;
    justify-items: center;
    width: 100%;
  }
  .card-bottom .grid{
    width: 100%;
  }
}
</style>
