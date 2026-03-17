<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
const cidade = "Tubarão, SC"
const escola = "Senai"
const nome = "Nome "
const idade = 18
const filme1 = "Capitão América o Soldado Invernal"
const filme2 = "Inerestelar"
const filme3 = "Guardiões da galáxia"


function desabilitado(){
  return idade < 18;
}
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <button :disabled="desabilitado()" class="btn btn-primary">Teste habilitamentação</button>
        <h1>Ola mundo projeto vue {{ cidade }} {{ escola }}</h1>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur necessitatibus, hic ad aliquam iusto quam neque incidunt quia atque, aliquid ex enim facilis mollitia consequuntur molestias, dicta eveniet error ipsum!</p>
        <h4>{{ nome }} {{ idade }}</h4>
        <ol>
          <li>{{ filme1 }}</li>
          <li>{{ filme2 }}</li>
          <li>{{ filme3 }}</li>
        </ol>
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


