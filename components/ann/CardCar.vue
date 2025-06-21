<script setup lang="ts">

</script>

<template>
<div class="card">
  <img src="https://avatars.mds.yandex.net/get-altay/1666174/2a0000016df23d129806c6a94fc355370a70/XXL_height" alt="">

  <div class="card-content">
    <h3>ГАЗ Промтоварный фургон на базе ГАЗон NEXT</h3>
    <div class="flex">
      <div class="grid">
        <p class="left">
          Шасси, 5.9 л / 270 л. с. <br>
          Задний привод <br>
          МКПП <br>
          Дизельный
        </p>
      </div>

      <div class="grid">
        <p class="red"><slot name="liz"></slot></p>
        <p class="gray">1 Хозяин</p>
          <div class="right"><img src="/img/Cart.png" alt=""> <p class="order">Доступна для заказа</p></div>
      </div>
    </div>
    <button>Узнать цену ></button>
  </div>
</div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');
*{
  margin: 0;
  padding: 0;
  font-family: 'Montserrat';
}
.card{
  border: 1px solid #545454;
  border-radius: 10px;
  max-width: 400px;
  height: 400px;
}
.card-content{
  display: grid;
  justify-items: center;
  padding: 10px;
  height: 200px;
  align-content: space-between;
}
h3{
  font-size: 1rem;
  font-weight: 500;
  text-align: center;
}
.grid{
  display: grid;
  font-size: 0.9rem;
}
.flex{
  display: flex;
  width: 100%;
  justify-content: space-between;
  margin-top: 10px;
  margin-bottom: 10px;
}
img{
  height: 170px;
  width: 100%;
  border-radius: 10px 10px 0 0;
  object-fit: cover;
}
.right img{
  height: 30px;
  width: 40px;
}
.right{
  display: flex;
  align-items: center;
}
.grid:nth-child(2){
  justify-items: end;
}
button{
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
.red{
  background: #880003;
  color: #fff;
  padding: 5px 20px 5px 20px;
  border-radius: 5px;
  font-weight: 500;
}
.gray{
  background: #1C1919;
  color: #fff;
  padding: 6px 15px 6px 15px;
  border-radius: 5px;
  font-weight: 500;
  margin-top: 5px;
  margin-bottom: 10px;
}
</style>