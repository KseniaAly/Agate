<script setup lang="ts">
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
        <img src="https://i.ytimg.com/vi/WlAWWnYWXcE/maxresdefault.jpg" alt="">
        <div class="card-content">
          <h3>{{ carSelect.name }}</h3>
          <div class="flex">
            <div class="grid">
              <p class="left">
                {{ carSelect.gender }} <br>
                {{ carSelect.species }} <br>
                {{ carSelect.dateOfBirth }} <br>
              </p>
            </div>
            <div class="grid">
              <p class="red">{{ carSelect.house }}</p>
              <p class="gray">{{ carSelect.house }}</p>
              <div class="right">
                <img src="/img/Cart.png" alt="">
                <p class="order">Доступна для заказа</p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="card-bottom">
        <div class="grid">
          <p class="left">
            {{ carSelect.gender }} <br>
            {{ carSelect.species }} <br>
            {{ carSelect.dateOfBirth }} <br>
            {{ carSelect.gender }} <br>
            {{ carSelect.species }} <br>
            {{ carSelect.dateOfBirth }} <br>
          </p>
        </div>
      </div>

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
  padding: 20px;
  width: 80%;
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
  margin-top: 10px;
}

.grid {
  display: grid;
  font-size: 1rem;
  margin-top: 10px;
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

.red {
  background: #880003;
  color: #fff;
  padding: 5px 20px 5px 20px;
  border-radius: 5px;
  font-weight: 500;
  text-align: center;
}

.gray {
  background: #1C1919;
  color: #fff;
  padding: 5px 20px 5px 20px;
  border-radius: 5px;
  font-weight: 500;
  margin-top: 5px;
  margin-bottom: 10px;
  text-align: center;
}

.left {
  color: #333333;
}

@media (max-width: 980px) {
  .card{
    display: grid;
  }
  img{
    width: 100%;
  }
}
</style>
