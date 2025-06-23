<script setup>
import {ref} from "vue";

defineProps({
  img:{
    type: Object,
    required: true
  }
})

const click = ref(false);

function press(){
  click.value = true;
}
function remove(){
  click.value = false;
}
</script>

<template>
  <div class="brand" @click="press" :class="{pressed: click}">
    <i class="fa-solid fa-xmark" v-if="click" @click.stop @click="remove"></i>
    <img :src="img.src">
  </div>
</template>

<style scoped>
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css";
.brand{
  display: flex;
  justify-content: center;
  width: 160px;
  height: 130px;
  margin-bottom: 20px;
}
.fa-xmark{
  position: absolute;
  background-color: #880003;
  color: white;
  border-radius: 2px;
  padding: 3px 5px;
  transform: translateX(63px);
  margin-top: 7px;
}
.pressed{
  background-color: #FCECEC;
}
@media (max-width: 768px) {
  .brand{
    display: flex;
    justify-content: center;
    width: 120px;
    height: 100px;
    padding: 10px 0;
    margin-right: 5px;
    box-sizing: border-box;
  }
  .brand img{
    width: 100px;
  }
  .fa-xmark{
    position: absolute;
    background-color: #880003;
    color: white;
    border-radius: 2px;
    padding: 3px 5px;
    transform: translateX(45px);
    margin-top: -5px;
    font-size: 12px;
  }
}
</style>