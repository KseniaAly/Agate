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
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css"
        integrity="sha512-z3gLpd7yknf1YoNbCzqRKc4qyor8gaKU1qmn+CShxbuBusANI9QpRohGBreCFkKxLhei6S9CQXFEbbKuqLg0DA=="
        crossorigin="anonymous" referrerpolicy="no-referrer"/>

  <div class="brand" @click="press" :class="{pressed: click}">
    <i class="fa-solid fa-xmark" v-if="click" @click.stop @click="remove"></i>
    <img :src="img.src">
  </div>
</template>

<style scoped>
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
</style>