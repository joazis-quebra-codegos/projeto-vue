<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
const cidade = "Tubarão, SC"
const escola = "Senai"
const nome = "Nome "
const idade = 19
const filme1 = "Capitão América o Soldado Invernal"
const filme2 = "Inerestelar"
const filme3 = "Guardiões da galáxia"


function desabilitado(){
  return idade < 18;
}

function salvarHabilitado(){
  return false;
}

function exibirAviso(){
  alert("oi")
}

function mudouSelect(event: Event){
  alert((event.target as HTMLSelectElement).value)
}

function mudouTexto(event: Event){
  return ((event.target as HTMLSelectElement).value)
}

</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <button @click="exibirAviso" :disabled="desabilitado()" class="btn btn-primary">Teste habilitamentação</button>
        <br> 
        <select @change="mudouSelect($event)" class="form-select" name="teste">
          <option value="1">Valor 1</option>
          <option value="2">Valor 2</option>
          <option value="3">Valor 3</option>
        </select>
        
        <h1>Ola mundo projeto vue {{ cidade }} {{ escola }}</h1>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur necessitatibus, hic ad aliquam iusto quam neque incidunt quia atque, aliquid ex enim facilis mollitia consequuntur molestias, dicta eveniet error ipsum!</p>
        <h4>{{ nome }} {{ idade }}</h4>
        <ol>
          <li>{{ filme1}}</li>
          <li>{{ filme2 }}</li>
          <li>{{ filme3 }}</li>
        </ol>

        <input type="text">

        <h1 @change="mudouTexto($event)" class="" name=""></h1>

        <h1></h1>
      </div>
    </div>
  </div>
</template>

<style>
.container{
  align-items:flex-start;
  justify-content: center;
}

h1{
  color: rgb(28, 28, 75);
}

p {
  font-style: italic;
}

</style>


