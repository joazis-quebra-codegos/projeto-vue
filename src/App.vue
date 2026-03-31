<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import { computed, ref } from 'vue'
const idade = 19
const valor = ref("")
const rolav = computed(() => {
  return valor.value.split('').reverse().join('') 
})

const visivel = true
const invisivel = false

const visivelLegal = ref(true)
const temperaturamento = ref(0)
const valorTemperatura = computed(Temperatura)

const ordenacao = ref('C')
const carros = ref(['Ferrari', 'Porsche'])
const nomeCarro = ref('')


function adicionarItemLista(){
  carros.value.push(nomeCarro.value)

  nomeCarro.value = ''

  ordemLista()
}

function ordemLista(){
  if (ordenacao.value == 'C'){
    carros.value.sort((a, b) => a.localeCompare(b))
  } else {
    carros.value.sort((a, b) => b.localeCompare(a))
  }
}

function apagarItemLista(index: number){
  carros.value.splice(index, 1)
}

function desabilitado(){
  return idade < 18;
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
      <div class="col">
        <button @click="exibirAviso" :disabled="desabilitado()" class="btn btn-primary">Teste habilitamentação</button>
        <br> 
        <select @change="mudouSelect($event)" class="form-select" name="teste">
          <option value="1">Valor 1</option>
          <option value="2">Valor 2</option>
          <option value="3">Valor 3</option>
        </select>

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


        <label for="">Ordenação</label>

        <input @keyup.enter="adicionarItemLista" placeholder="Nome do carro" type="text" class="form-control" v-model="nomeCarro">

        <select @change="ordemLista" name="" id="" v-model="ordenacao">
          <option value="C" >Crescente</option>
          <option value="D" >Decresente</option>
        </select>

        <table border='1'>
          <thead>
            <tr>
              <th >Carros</th>
              <th>Apagar</th>
            </tr>
          </thead>

            <tbody>
            <tr v-for="(carro, index) in carros" :key="carro">
              <td>{{ carro }}</td>
              <td>
                <button @click="apagarItemLista(index)" id="botao"></button>
              </td>
            </tr>
            </tbody>
          </table>

      </div>
    </div>
  </div>
</template>

<style>
body{
  gap: 5px;
}
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

#botao{
  width: 30px;
  height: 15px;
}

</style>


