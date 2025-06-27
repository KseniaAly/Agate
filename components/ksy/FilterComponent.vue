<script setup>
import { ref } from 'vue'

const emit = defineEmits(['update'])
const link = ref('/api/instock/?city_id=27&auto_type=3847')

function filter_transmission() {
  const akpp = document.querySelector('#akpp')?.checked
  const mkpp = document.querySelector('#mkpp')?.checked

  if (akpp) {
    link.value = link.value+'&property_transmission=АКПП'
  } else if (mkpp) {
    link.value = link.value+'&property_transmission=МКПП'
  } else if(!akpp){
    link.value = link.value.replace('&property_transmission=АКПП', '')
  } else if(!mkpp){
    link.value = link.value.replace('&property_transmission=МКПП', '')
  }
  emit('update', link.value)
}

function removeFilter(){
  link.value = '/api/instock/?city_id=27&auto_type=3847'
  emit('update', link.value)
}

function wes() {
  link.value = '/api/instock/?city_id=27&auto_type=3847&property_gross_weight=2800'
  emit('update', link.value)
}

function press(element){
  let buttons = document.querySelectorAll(".btn")
  for (let button of buttons){
    button.classList.remove('pressed')
  }
  element.target.classList.add('pressed')
}
function click(element){
  if (element.target.classList.contains('select')){
    if(element.target.lastElementChild.classList.contains('focus')){
      element.target.lastElementChild.classList.remove('focus')
      element.target.firstElementChild.firstElementChild.classList.remove('rotate')
    } else {
      element.target.lastElementChild.classList.add('focus')
      element.target.firstElementChild.firstElementChild.classList.add('rotate')
    }
  }else if(element.target.tagName === 'P' || element.target.tagName === 'I'){
    if(element.target.parentElement.nextElementSibling.classList.contains('focus')){
      element.target.parentElement.nextElementSibling.classList.remove('focus')
      if(element.target.tagName === 'P'){
        element.target.previousElementSibling.classList.remove('rotate');
      } else {
        element.target.classList.remove('rotate')
      }
    } else {
      element.target.parentElement.nextElementSibling.classList.add('focus')
      if(element.target.tagName === 'P'){
        element.target.previousElementSibling.classList.add('rotate');
      } else {
        element.target.classList.add('rotate')
      }
    }
  }
}
function click_second(element){
  if (element.target.classList.contains('select')){
    if(element.target.lastElementChild.classList.contains('focus_second')){
      element.target.lastElementChild.classList.remove('focus_second')
      element.target.firstElementChild.firstElementChild.classList.remove('rotate')
    } else {
      element.target.lastElementChild.classList.add('focus_second')
      element.target.firstElementChild.firstElementChild.classList.add('rotate')
    }
  }else if(element.target.tagName === 'P' || element.target.tagName === 'I'){
    if(element.target.parentElement.nextElementSibling.classList.contains('focus_second')){
      element.target.parentElement.nextElementSibling.classList.remove('focus_second')
      if(element.target.tagName === 'P'){
        element.target.previousElementSibling.classList.remove('rotate');
      } else {
        element.target.classList.remove('rotate')
      }
    }else {
      element.target.parentElement.nextElementSibling.classList.add('focus_second')
      if(element.target.tagName === 'P'){
        element.target.previousElementSibling.classList.add('rotate');
      } else {
        element.target.classList.add('rotate')
      }
    }
  }
}
</script>

<template>
  <div class="body">
    <h3>Подобрать технику</h3>
    <div class="buttons">
      <button class="btn pressed" @click="press">Все</button>
      <button class="btn" @click="press">Спецтехника</button>
      <button class="btn" @click="press">Комтехника</button>
    </div>
    <div class="select brand" @click="click">
      <div class="name">
        <i class="fa-solid fa-chevron-up"></i>
        <p>Бренд</p>
      </div>
      <div class="content scroll">
        <p id="GAZ">Газ</p>
        <p id="KAMAZ">Kamaz</p>
        <p id="HINO">HINO</p>
        <p id="MAZ">MAZ</p>
        <p id="GTRUCKS">Daewoo Trucks</p>
        <p id="SHACMAN">SHACMAN</p>
      </div>
    </div>
    <div class="line brand"></div>
    <div class="select" @click="click">
      <div class="name">
        <i class="fa-solid fa-chevron-up"></i>
        <p>Продукция</p>
      </div>
      <div class="content scroll">
        <p>Борт</p>
        <p>Фургон</p>
        <p>Цельнометаллический фургон</p>
      </div>
    </div>
    <div class="line"></div>
    <div class="select" @click="click_second">
      <div class="name">
        <i class="fa-solid fa-chevron-up"></i>
        <p>Коробка передач</p>
      </div>
      <div class="content">
        <input type="checkbox" id="mkpp" @change="filter_transmission">
        <label for="mkpp">МКПП</label>
        <input type="checkbox" id="akpp" @change="filter_transmission">
        <label for="akpp">АКПП</label>
      </div>
    </div>
    <div class="line"></div>
    <div class="select" @click="click">
      <div class="name">
        <i class="fa-solid fa-chevron-up"></i>
        <p>Двигатель</p>
      </div>
      <div class="content">
        <h5>Мощность, л.с.</h5>
        <div class="buttons">
          <button>до 100</button>
          <button>100-150</button>
          <button>150-200</button>
          <button>200+</button>
        </div>
        <h5>Тип двигателя</h5>
        <div class="check">
          <div class="input">
            <input type="checkbox" id="petrol">
            <label for="petrol">Бензиновый</label>
          </div>
          <div class="input">
            <input type="checkbox" id="diesel">
            <label for="diesel">Дизельный</label>
          </div>
          <div class="input">
            <input type="checkbox" id="gas">
            <label for="gas">Газовый</label>
          </div>
        </div>
      </div>
    </div>
    <div class="line"></div>
    <div class="select" @click="click">
      <div class="name">
        <i class="fa-solid fa-chevron-up"></i>
        <p>Привод</p>
      </div>
      <div class="content scroll">
        <p>Задний</p>
        <p>Передний</p>
        <p>Полный</p>
      </div>
    </div>
    <div class="line"></div>
    <p class="link_button" id="remove" @click="removeFilter">Сбросить параметры фильтра</p>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');
*{
  display: block;
  font-family: 'Montserrat';
}
.btn{
  cursor: pointer;
  margin-right: 5px;
}
h3{
  color: #333333;
  font-size: 16px;
  text-align: center;
  margin: 0;
}
  .body{
    padding: 30px 17px;
    border: 3px solid #880003;
    border-radius: 5px;
    width: fit-content;
    height: fit-content;
  }
  .name{
    display: flex;
    align-items: baseline;
    margin-bottom: 10px;
  }
  .name p{
    font-size: 14px;
    margin: 0;
    margin-left: 8px;
    color: #333333;
  }
  .name i{
    color: #D51317;
  }
  .buttons{
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
    margin-top: 15px;
  }
  .buttons button{
    border: none;
    border-radius: 5px;
    padding: 5px 10px;
    background-color: #FCECEC;
    font-size: 13px;
  }
  .buttons button.pressed{
    background-color: #1C1919;
    color: white;
  }
  .line{
    background-color: #DADADA;
    height: 1px;
    margin: 15px 0;
    width: 100%;
  }
  .link_button{
    font-size: 14px;
    margin: 0;
    color: #880003;
    text-decoration: underline;
    cursor: pointer;
  }
  .input{
    margin-bottom: 5px;
  }
input[type="checkbox"]{
  padding: 9px;
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
  .select:nth-child(5) .content{
    align-items: center;
  }
  .select:nth-child(5) .content label{
    font-size: 12px;
    margin-left: 5px;
  }
  #akpp{
    margin-left: 70px;
  }
  .scroll{
    border: 1px solid #333333;
    width: 15rem;
    height: 120px;
    overflow-y: scroll;
    padding: 0 15px;
    border-radius: 5px;
  }
  .scroll p{
    margin: 20px 0;
    font-size: 14px;
    color: #1C1919;
  }
  .scroll p:hover{
    cursor: pointer;
    color: #880003;
  }
  .scroll::-webkit-scrollbar {
    width: 7px;
    background-color: #F0F0F0;
    border-radius: 5px;
  }
  .scroll::-webkit-scrollbar-thumb {
    background: linear-gradient(180deg, #D51317, #880003);
    border-radius: 5px;
  }
  h5{
    margin: 0;
    font-size: 14px;
    font-weight: 400;
    color: #333333;
  }
  .content .buttons{
    width: 220px;
    flex-wrap: wrap;
    margin-top: 10px;
    margin-bottom: 10px;
  }
  .content .buttons button{
    width: fit-content;
    padding: 6px 11px;
    margin-bottom: 7px;
    background-color: white;
    border: 1px solid #DADADA;
    color: #1C1919;
  }
  .content .buttons button:hover{
    background-color: #D51317;
    border: 1px solid #D51317;
    color: white;
  }
  .check{
    margin-top: 10px;
  }
  .check .input{
    display: flex;
    align-items: center;
  }
  .check .input label{
    font-size: 14px;
    color: #333333;
    margin-left: 5px;
  }
label{
  font-size: 14px;
}
  .content{
    display: none;
  }
  .select{
    position: relative;
    display: inline-block;
  }
  .name:hover{
    cursor: pointer;
  }
  .focus{
    display: block;
  }
  .focus_second{
    display: flex;
  }
  .select .name i{
    transform: rotate(180deg);
    transition: 0.3s;
  }
  .rotate{
    transform: rotate(0) !important;
  }

  .brand{
    display: none;
  }

input[type="checkbox"]{
  margin-right: 5px;
}

@media (max-width: 480px) {
  .brand{
    display: block;
  }
  .body{
    position: absolute;
    background-color: white;
  }
}
</style>