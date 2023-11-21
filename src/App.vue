<script setup>

import {ref, computed} from "vue"

const contador=ref(0);
const favorito = ref([]);
  
const sumar=()=>{
    contador.value++
};

const restar=()=>{
    contador.value--
};

const reinicar=()=>{
    contador.value=0
};

const agregar=()=>{
    favorito.value.push(contador.value)
    console.log(favorito)
};

const bloquear=computed(()=>{
    const repetido = favorito.value.find(numero=>numero===contador.value)
    if(repetido===0){return true}
    return repetido ? true : false ;
})

</script>

<template>
  <div id="flex" class="container text-center">
    <h1 style="color: green;" v-if="contador>0">{{ contador }}</h1>
    <h1 style="color: red;" v-if="contador<=0">{{ contador }}</h1>

    <div class="btn-group" role="group" aria-label="Basic mixed styles example">
      <button @click="sumar" class="btn btn-success">sumar</button>
      <button @click="restar" class="btn btn-danger">restar</button>
      <button @click="reinicar" class="btn btn-secondary">reiniciar contador</button>
      <button @click="agregar" :disabled="bloquear" class="btn btn-primary">favorito</button>
    </div>
      
      <ul class="list-group">
          <li class="list-group-item" v-for="fav in favorito">
            {{ fav }}
          </li> 
      </ul>
  </div>
</template>

<style>
 
</style>