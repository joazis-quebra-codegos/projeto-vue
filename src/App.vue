<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { computed, ref, VueElement } from 'vue'
const funcionario = ref('')
const valor = ref(0)
const valorReajuste = ref(0)
const funcInverter = ref(true)
const produtos = ref([
  {
    id: 1,
    nome: "Notebook Dell inspiron",
    preco: 3499.00,
    descricao: "Notebook bom",
    peso: 1.8
  },
  {
    id: 2,
    nome: "Celular ajax",
    preco: "2.99",
    descricao: "Celular da marca ajax",
    peso: 0
  },
  {
    id: 2,
    nome: "Air fryer",
    preco: 3.99,
    descricao: "Melhor item doméstico iventando na história da humanidade",
    peso: 0.1
  }
])

function inverter(){
    funcionario.value = funcionario.value.split('').reverse().join('')
}

function verificar(){
  if (valorReajuste.value < 0 || valorReajuste.value > 100){
    return false
  } else{
    return true
  }
}

</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <h5>Nome do funcionario</h5>
        <input class="form-control" placeholder="digite o funcionario aqui" v-model="funcionario">
        <h5>Salario</h5>
        <input type="number" class="form-control" placeholder="digite o funcionario aqui" v-model="valor">
        <h5>Reajuste salarial</h5>
        <input @input="verificar" type="number" class="form-control" placeholder="digite o funcionario aqui" v-model="valorReajuste">
        
        <h2>{{ funcionario }}</h2>
        <p v-if="!verificar()">Ajuste excede os limites!</p>
        <h2>Valor reajustado: {{ valor/1 + (valor * valorReajuste/100) }}</h2>

        <button @click="inverter()">Inverter funcionario</button>
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


