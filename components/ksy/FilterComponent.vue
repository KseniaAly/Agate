<script setup>
import { ref } from 'vue'

const emit = defineEmits(['update'])
let link = ref('/api/instock/?city_id=27&auto_type=3847')

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

function bort() {
  link.value.replace('&property_body_type=Фургон', '')
  link.value.replace('&property_body_type=Цельнометаллический фургон', '')
  link.value = link.value+'&property_body_type=Борт'
  emit('update', link.value)
}

function fur() {
  link.value.replace('&property_body_type=Борт', '')
  link.value.replace('&property_body_type=Цельнометаллический фургон', '')
  link.value = link.value+'&property_body_type=Фургон'
  emit('update', link.value)
}

function chfur() {
  link.value.replace('&property_body_type=Фургон', '')
  link.value.replace('&property_body_type=Борт', '')
  link.value = link.value+'&property_body_type=Цельнометаллический фургон'
  emit('update', link.value)
}

function zadn() {
  link.value.replace('&property_gear_type=Передний', '')
  link.value.replace('&property_gear_type=Полный', '')
  link.value = link.value+'&property_gear_type=Задний'
  emit('update', link.value)
}

function pered() {
  link.value.replace('&property_gear_type=Задний', '')
  link.value.replace('&property_gear_type=Полный', '')
  link.value = link.value+'&property_gear_type=Передний'
  emit('update', link.value)
}

function poln() {
  link.value.replace('&property_gear_type=Передний', '')
  link.value.replace('&property_gear_type=Задний', '')
  link.value = link.value+'&property_gear_type=Полный'
  emit('update', link.value)
}

function none() {
  link.value = '/api/instock/?city_id=27&auto_type=3847'
  emit('update', link.value)
  const akpp = document.querySelector('#akpp')
  const mkpp = document.querySelector('#mkpp')
  akpp.checked = false;
  mkpp.checked = false;
  const petrol = document.querySelector('#petrol')
  const diesel = document.querySelector('#diesel')
  const gas = document.querySelector('#gas')
  petrol.checked = false;
  diesel.checked = false;
  gas.checked = false;
  let buttons = document.querySelectorAll(".type-car3")
  for (let button of buttons){
    if(button.classList.contains('activeButton')){
      button.classList.remove('activeButton')
    }
  }
}

function filter_engineType() {
  const petrol = document.querySelector('#petrol')?.checked
  const diesel = document.querySelector('#diesel')?.checked
  const gas = document.querySelector('#gas')?.checked

  if (petrol) {
    link.value = link.value+'&property_engine_type=Бензиновый'
  } else if(!petrol){
    link.value = link.value.replace('property_engine_type=Бензиновый', '')
  }
  if (diesel) {
    link.value = link.value+'&property_engine_type=Дизельный'
  } else if(!diesel){
    link.value = link.value.replace('&property_engine_type=Дизельный', '')
  }
  if (gas) {
    link.value = link.value+'&property_engine_type=Газовый'
  } else if(!gas){
    link.value = link.value.replace('&property_engine_type=Газовый', '')
  }
  if (petrol && gas){
    link.value = link.value+'&property_engine_type=Бензиновый/Газовый'
  } else {
    link.value = link.value.replace('&property_engine_type=Бензиновый/Газовый', '')
  }

  emit('update', link.value)
}

function applyEnginePower(min, max) {
  link.value = link.value.replace(/&property_engine_power_min=\d+/g, '')
  link.value = link.value.replace(/&property_engine_power_max=\d+/g, '')

  if (min !== null) link.value += `&property_engine_power_min=${min}`
  if (max !== null) link.value += `&property_engine_power_max=${max}`

  emit('update', link.value)
}

function buttonClickedOne(){
  let buttons = document.querySelectorAll(".type-car3")
  for (let button of buttons){
    if(button.classList.contains('activeButton')){
      button.classList.remove('activeButton')
    }
  }
  let element = document.querySelector("#one");
  element.classList.add('activeButton')
}
function buttonClickedTwo(){
  let buttons = document.querySelectorAll(".type-car3")
  for (let button of buttons){
    if(button.classList.contains('activeButton')){
      button.classList.remove('activeButton')
    }
  }
  let element = document.querySelector("#two");
  element.classList.add('activeButton')
}
function buttonClickedThree(){
  let buttons = document.querySelectorAll(".type-car3")
  for (let button of buttons){
    if(button.classList.contains('activeButton')){
      button.classList.remove('activeButton')
    }
  }
  let element = document.querySelector("#three");
  element.classList.add('activeButton')
}
function buttonClickedFour(){
  let buttons = document.querySelectorAll(".type-car3")
  for (let button of buttons){
    if(button.classList.contains('activeButton')){
      button.classList.remove('activeButton')
    }
  }
  let element = document.querySelector("#four");
  element.classList.add('activeButton')
}

//Для раскрытия
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
        <button class="type-car" @click="bort">Борт</button>
        <button class="type-car" @click="fur">Фургон</button>
        <button class="type-car" @click="chfur">Цельнометаллический фургон</button>
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
          <button class="type-car3" @click="applyEnginePower(0, 100); buttonClickedOne()" id="one">до 100</button>
          <button class="type-car3" @click="applyEnginePower(100, 125); buttonClickedTwo()" id="two">100-125</button>
          <button class="type-car3" @click="applyEnginePower(125, 200); buttonClickedThree()" id="three">125-200</button>
          <button class="type-car3" @click="applyEnginePower(201, null); buttonClickedFour()" id="four">200+</button>
        </div>
        <h5>Тип двигателя</h5>
        <div class="check">
          <div class="input">
            <input type="checkbox" id="petrol" @change="filter_engineType">
            <label for="petrol">Бензиновый</label>
          </div>
          <div class="input">
            <input type="checkbox" id="diesel" @change="filter_engineType">
            <label for="diesel">Дизельный</label>
          </div>
          <div class="input">
            <input type="checkbox" id="gas" @change="filter_engineType">
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
        <button class="type-car2" @click="zadn">Задний</button>
        <button class="type-car2" @click="pered">Передний</button>
        <button class="type-car2" @click="poln">Полный</button>
      </div>
    </div>
    <div class="line"></div>
    <button class="link_button" @click="none">Сбросить параметры фильтра</button>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');
*{
  display: block;
  font-family: 'Montserrat';
}
.content .type-car3.activeButton{
  background-color: #D51317;
  color: white;
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
    background: none;
    border: none;
    transition: 0.3s;
  }
.link_button:hover {
  cursor: pointer;
  color: black;
  transition: 0.3s;
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
  .scroll p, .type-car, .type-car2{
    background: none;
    border: none;
    text-align: start;
    margin: 20px 0;
    font-size: 14px;
    color: #1C1919;
  }
.type-car:hover, .type-car2:hover{
  color: #880003;
  cursor: pointer;
  font-weight: 500;
}

.type-car:focus, .type-car2:focus{
  color: #880003;
  cursor: pointer;
  font-weight: 500;
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
  .content .type-car3{
    width: fit-content;
    padding: 6px 11px;
    margin-bottom: 7px;
    background-color: white;
    border: 1px solid #DADADA;
    color: #1C1919;
  }
  .content .type-car3:hover{
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