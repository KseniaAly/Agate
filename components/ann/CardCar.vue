<script setup>

</script>

<template>
<div class="card">
  <slot name="img"></slot>

  <div class="card-content">
    <h3><slot name="h3"></slot></h3>
    <div class="flex">
      <div class="grid">
        <p class="left"><slot name="left"></slot> </p>
      </div>

      <div class="grid">
        <p class="red"><slot name="liz"></slot></p>
        <p class="gray"><slot name="hoz"></slot></p>
          <div class="right"><img src="/img/Cart.png" alt=""> <p class="order">Доступна для заказа</p></div>
      </div>
    </div>
    <slot name="button"></slot>
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
  width: 400px;
  height: 400px;
  cursor: pointer;
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
.red{
  background: #880003;
  color: #fff;
  padding: 5px 20px 5px 20px;
  border-radius: 5px;
  font-weight: 500;
  text-align: center;
  transition: 0.3s;
}
.red:hover{
  background-color: #9a3c3c;
  transition: 0.3s;
}
.gray{
  background: #1C1919;
  color: #fff;
  padding: 5px 20px 5px 20px;
  border-radius: 5px;
  font-weight: 500;
  margin-top: 5px;
  margin-bottom: 10px;
  text-align: center;
  transition: 0.3s;
}
.gray:hover{
  background: #4a4a4a;
  transition: 0.3s;
}
.left{
  color: #333333;
}

@media (max-width: 480px) {
.left, .right{
  display: none;
}
  .card-content{
    justify-content: center;
  }
  .flex{
    justify-content: center;
  }
}

@media (max-width: 400px) {
  .card{
    width: 350px;
  }
}

@media (max-width: 350px) {
  .card{
    width: 300px;
  }
}

@media (max-width: 300px) {
  .card{
    width: 250px;
  }
}
</style>