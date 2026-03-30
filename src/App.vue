<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import { computed, ref } from 'vue'
const cidade = "Tubarão, SC"
const escola = "Senai"
const nome = "Nome "
const idade = 19
const filme1 = "Capitão América o Soldado Invernal"
const filme2 = "Inerestelar"
const filme3 = "Guardiões da galáxia"

const valor = ref("")
const rolav = computed(() => {
  return valor.value.split('').reverse().join('') 
})

const visivel = true
const invisivel = false

const visivelLegal = ref(true)
const temperaturamento = ref(0)
const valorTemperatura = computed(Temperatura)

const carros = ref(['Audi', 'Corsa', 'Porsche', 'Chevette', 'Uno', 'Argo', 'Ferrari'])
const adCarro = ref('')

function adicionarCarro(){
  carros.value.push(adCarro.value)
}

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

function Temperatura(){
  if (temperaturamento.value < 10){
    return "⛷️⛷️⛷️"
  }
  else if (temperaturamento.value <= 25){
    return "🤺🤺🤺"
  }
  else if (temperaturamento.value <= 35){
    return "🥀🥀🥀"
  }
  else{
    return "🫠🫠🫠"
  }
}

</script>

<template>
  <div class="container">
    <div class="row">
      <div v-if="visivel" class="col">
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

        <input type="text" class="form=control" v-model="valor">

        <h1 v-if="invisivel">{{ valor }}</h1>
        <h1 v-else-if="visivel">{{ rolav }}</h1>
        <h1 v-else="">mensagem</h1>

        <div class="mb-3 form-check">
          <input v-model="visivelLegal" type="checkbox" class="form-check-input">
          <label class="form-check-label">Visivel com vshow</label>
        </div>
        <h1 v-show="visivelLegal">Só visivel quando marcado</h1>

        <input type="text" class="form-control" v-model="temperaturamento">
        <h1>{{valorTemperatura}}</h1>

        <input @keyup.enter="adicionarCarro" type="text" class="form-control" v-model="adCarro">

        <ul>
          <li v-for="carro in carros" :key="carro">
            {{ carro }}
          </li>
        </ul>
  
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


