<script setup>
import ButtonVue from "~/components/ksy/ButtonVue.vue";

defineProps({
  open:{
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['close'])
function close(){
  emit('close', false);
}
</script>

<template>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css"
        integrity="sha512-z3gLpd7yknf1YoNbCzqRKc4qyor8gaKU1qmn+CShxbuBusANI9QpRohGBreCFkKxLhei6S9CQXFEbbKuqLg0DA=="
        crossorigin="anonymous" referrerpolicy="no-referrer"/>

  <div class="background" v-if="open">
    <div class="content">
      <div class="head">
        <img src="/img/logo.svg">
        <i class="fa-solid fa-xmark" @click="close"></i>
      </div>
      <div class="body">
        <h1>Оставить заявку</h1>
        <div class="inputs">
          <input placeholder="ФИО *">
          <input placeholder="Телефон *">
          <input placeholder="Email *">
          <input class="message" placeholder="Комментарий">
        </div>
        <div class="foot">
          <div class="checkbox">
            <input id="checkbox" type="checkbox" checked>
            <label for="checkbox">Даю согласие на обработку персональных данных и подтверждаю, что ознакомлен с
              политикой обработки персональных данных</label>
          </div>
          <button-vue class="button-vue"/>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css";
*{
  font-family: Monserrat;
}

.head{
  background-color: #1C1919;
  padding: 20px;
  border-top-left-radius: 16px;
  border-top-right-radius: 16px;
  display: flex;
  justify-content: space-between;
}
.fa-xmark{
  background-color: #880003;
  color: white;
  border-radius: 2px;
  padding: 3px 5px;
  height: fit-content;
}
.background{
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background: rgba(0,0,0,0.5);
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 100;
}
.content{
  background-color: #fff;
  border-radius: 20px;
  width: 80%;
  border: 4px solid #880003;
}
h1{
  padding: 30px;
  font-weight: 400;
  font-size: 28px;
  color: #333333;
  margin: 0;
}
input{
  padding: 20px;
  font-size: 20px;
  font-weight: 400;
  border: 2px solid #545454;
  margin-bottom: 10px;
  border-radius: 5px;
  color: #333333;
}
.inputs{
  display: flex;
  flex-direction: column;
  margin-left: 30px;
  margin-right: 30px;
}
.message{
  height: 140px;
}
.message::placeholder{
  transform: translateY(-50px);
}
input::placeholder{
  transition: all 0.5s ease-in-out;
}
input:focus::placeholder{
  transform: translateY(-20px);
  font-size: 14px;
}
.message:focus::placeholder{
  transform: translateY(-55px);
}
input[type="checkbox"]{
  padding: 10px;
  appearance: none;
  position: relative;
  width: 0;
  height: 0;
  background: #D51317;
  border-radius: 5px;
  transition: 0.5s;
  border: none;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: 30px;
}
input[type="checkbox"]::after{
  content: "";
  position: absolute;
  width: 30px;
  height: 0;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' height='16' viewBox='0 -960 960 960' width='30' stroke='%23FFFFFF' stroke-width='30' fill='%23FFFFFF'%3E%3Cpath d='M382-240 154-468l57-57 171 171 367-367 57 57-424 424Z'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  transition: 0.5s;
}
input[type="checkbox"]:checked::after{
  width: 30px;
  height: 16px;
  transition: 0.5s;
}
.foot{
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
}
.checkbox{
  display: flex;
  align-items: center;
  text-align: left;
}
.checkbox label{
  margin-left: 10px;
  font-size: 16px;
  color: #333333;
  font-weight: 600;
  transform: translateY(-5px);
  width: 80%;
}
.button-vue{
  margin-right: 30px;
}
</style>