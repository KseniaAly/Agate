<script setup>
import ButtonVue from "~/components/ksy/ButtonVue.vue";
import {reactive, ref} from "vue";

defineProps({
  open:{
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['close']);
function close(){
  emit('close', false);
}

const errors = reactive({
  errorName: false,
  errorPhone: false,
  errorEmail: false,
})

const formModal = reactive({
  name: '',
  phone: '',
  email: ''
})

const errorName = reactive({
  name: '',
  phone: '',
  email: ''
})

function checkName(){
  let reg = /^[a-zA-Zа-яА-Я]{3,25}$/;
  if(formModal.name === ''){
    errors.errorName = true;
    errorName.name = 'Это обязательное поле для заполнения';
  } else {
    if(reg.test(formModal.name)){
      errors.errorName = false;
    } else {
      errors.errorName = true;
      errorName.name = 'Только буквы (3-25 символов)';
    }
  }
}
function checkPhone(){
  let reg = /^(\+7|8)\([0-9]{3}\)[0-9]{3}-[0-9]{2}-[0-9]{2}$/;
  if(formModal.phone === ''){
    errors.errorPhone = true;
    errorName.phone = 'Это обязательное поле для заполнения';
  } else {
    if(reg.test(formModal.phone)){
      errors.errorPhone = false;
    } else {
      errors.errorPhone = true;
      errorName.phone = '8(+7)(###)###-##-##';
    }
  }
}
function checkEmail(){
  let reg = /^[a-zA-Z0-9]+@(mail.ru|gmail.com|yandex.ru)$/;
  if(formModal.email === ''){
    errors.errorEmail = true;
    errorName.email = 'Это обязательное поле для заполнения';
  } else {
    if(reg.test(formModal.email)){
      errors.errorEmail = false;
    } else {
      errors.errorEmail = true;
      errorName.email = 'Некорректный email';
    }
  }
}

const submite = ref(false);
function send(){
  let regName = /^[a-zA-Zа-яА-Я]{3,25}$/;
  let regPhone = /^(\+7|8)\([0-9]{3}\)[0-9]{3}-[0-9]{2}-[0-9]{2}$/;
  let regEmail = /^[a-zA-Z0-9]+@(mail.ru|gmail.com|yandex.ru)$/;
  let error = false;
  if(formModal.name === ''){
    errors.errorName = true;
    errorName.name = 'Это обязательное поле для заполнения'
    error = true
  } else {
    if(regName.test(formModal.name)){
      errors.errorName = false;
      error = false
    } else {
      errors.errorName = true;
      errorName.name = 'Только буквы (3-25 символов)';
      error = true
    }
  }
  if(formModal.phone === ''){
    errors.errorPhone = true;
    errorName.phone = 'Это обязательное поле для заполнения';
    error = true
  } else {
    if(regPhone.test(formModal.phone)){
      errors.errorPhone = false;
      error = false
    } else {
      errors.errorPhone = true;
      errorName.phone = '8(+7)(###)###-##-##';
      error = true
    }
  }
  if(formModal.email === ''){
    errors.errorEmail = true;
    errorName.email = 'Это обязательное поле для заполнения';
    error = true
  } else {
    if(regEmail.test(formModal.email)){
      errors.errorEmail = false;
      error = false
    } else {
      errors.errorEmail = true;
      errorName.email = 'Некорректный email';
      error = true
    }
  }
  if (!error){
    submite.value = true;
    setTimeout(() => emit('close', false), 1500);
    setTimeout(() => submite.value = false, 1500);
    formModal.name = '';
    formModal.phone = '';
    formModal.email = '';
  }
}
</script>

<template>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css"
        integrity="sha512-z3gLpd7yknf1YoNbCzqRKc4qyor8gaKU1qmn+CShxbuBusANI9QpRohGBreCFkKxLhei6S9CQXFEbbKuqLg0DA=="
        crossorigin="anonymous" referrerpolicy="no-referrer"/>

  <div class="background" v-if="open">
    <div class="successMessage" v-if="submite">
      Форма успешно отправлена! Мы свяжемся с вами в ближайшее время.
    </div>
    <form class="content" v-if="!submite">
      <div class="head">
        <img src="/img/logo.svg">
        <i class="fa-solid fa-xmark" @click="close"></i>
      </div>
      <div class="body">
        <h1>Оставить заявку</h1>
        <div class="inputs">
          <div class="input">
            <input type="text" placeholder="ФИО *" v-model="formModal.name" @focusout="checkName"
                   :class="{'error': errors.errorName}">
            <span v-if="errors.errorName">{{errorName.name}}</span>
          </div>
          <div class="input">
            <input placeholder="Телефон *" v-model="formModal.phone" @focusout="checkPhone"
                   :class="{'error': errors.errorName}">
            <span v-if="errors.errorPhone">{{errorName.phone}}</span>
          </div>
          <div class="input">
            <input placeholder="Email *" v-model="formModal.email" @focusout="checkEmail"
                   :class="{'error': errors.errorName}">
            <span v-if="errors.errorEmail">{{errorName.email}}</span>
          </div>
          <input class="message" placeholder="Комментарий">
        </div>
        <div class="foot">
          <div class="checkbox">
            <input id="checkbox" type="checkbox" checked>
            <label for="checkbox">Даю согласие на обработку персональных данных и подтверждаю, что ознакомлен с
              политикой обработки персональных данных</label>
          </div>
          <button class="button-vue" @click="send" type="button">Отправить ></button>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css";
*{
  font-family: Monserrat;
}

button{
  border: none;
  background-color: #880003;
  color: white;
  font-size: 14px;
  font-weight: 600;
  padding: 8px 122px;
  border-radius: 5px;
  width: 348px;
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
  font-size: 18px;
}

.successMessage{
  background-color: #fff;
  border-radius: 20px;
  width: 100%;
  border: 2px solid #880003;
  padding: 70px;
  font-size: 20px;
  color: #880003;
  font-weight: 700;
  text-align: center;
}
.error{
  border: 2px solid #D51317;
}

span{
  color: #D51317;
  margin-top: 5px;
  font-size: 12px;
}
.input{
  display: flex;
  flex-direction: column;
  margin-bottom: 10px;
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
  border-radius: 5px;
  color: #333333;
}
.inputs{
  display: flex;
  flex-direction: column;
  margin-left: 30px;
  margin-right: 30px;
  margin-bottom: 15px;
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
  width: 80%;
}
.button-vue{
  margin-right: 30px;
}
</style>