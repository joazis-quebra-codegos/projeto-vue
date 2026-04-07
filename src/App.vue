<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { computed, ref, VueElement } from 'vue'
import type Produto from './models/Produto'
import type Funcionario from './models/Funcionario'
const filtrados = ref([] as Funcionario[])
const busca = ref(0)

function filtrar(){
  if (busca.value != 0){
    filtrados.value = funcionarios.value.filter(funcionario => funcionario.id == busca.value)
  } else {
    filtrados.value = funcionarios.value
  }
}

function validar(){
  const erros: string[] = []

  if (!funcionario.value.nome){
    erros.push("Nome é obrigatório")
  }

  if (!funcionario.value.cpf){
    erros.push("CPF é obrigatório")
  }

  if (!funcionario.value.dataNascimento){
    erros.push("Data de nascimento é obrigatória")
  }

  if (!funcionario.value.email){
    erros.push("Email é obrigatório")
  }

  if (!funcionario.value.senha){
    erros.push("Senha é obrigatória")
  } else if (funcionario.value.senha.length < 8 || funcionario.value.senha.length > 64){
    erros.push("Senha deve ter entre 8 e 64 caracteres")
  }

  return erros
}

const erro = ref('')

function enviar(){
  const erros = validar()

  if (erros.length > 0){
    alert(erros.join('\n')) // quebra de linha
  } else {
    alert("Funcionário válido ✅")
  }
}

const funcionarios = ref([
  {
    id: 1,
    nome: "Carlos Silva",
    cpf: "123.456.789-10",
    email: "carlos.silva@email.com",
    dataNascimento: new Date("1990-05-12"),
    senha: "abc123",
    telefone: 11987654321
  },
  {
    id: 2,
    nome: "Ana Souza",
    cpf: "987.654.321-00",
    email: "ana.souza@email.com",
    dataNascimento: new Date("1985-09-30"),
    senha: "senha456",
    telefone: 11991234567
  },
  {
    id: 3,
    nome: "Lucas Pereira",
    cpf: "456.789.123-55",
    email: "lucas.p@email.com",
    dataNascimento: new Date("2000-01-20"),
    senha: "lucas789",
    telefone: 11999887766
  }
]as Funcionario[])

const funcionario = ref({} as Funcionario)

</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <form @submit.prevent="enviar">
          <div class="mb-3">
            <label for="form-label">Nome</label>
            <input v-model="funcionario.nome" class="form-control" type="text">
          </div>
                    <div class="mb-3">
            <label for="form-label">CPF</label>
            <input v-model="funcionario.cpf" class="form-control" type="text">
          </div>
                    <div class="mb-3">
            <label for="form-label">Data de nascimento</label>
            <input v-model="funcionario.dataNascimento" class="form-control" type="date">
          </div>
                    <div class="mb-3">
            <label for="form-label">Email</label>
            <input v-model="funcionario.email" class="form-control" type="text">
          </div>
                    <div class="mb-3">
            <label for="form-label">Senha</label>
            <input v-model="funcionario.senha" class="form-control" type="password">
          </div>
                    <div class="mb-3">
            <label for="form-label">Telefone</label>
            <input v-model="funcionario.telefone" class="form-control" type="text">
          </div>
        </form>

        <button @click="enviar" type="submit">Enviar </button>

        <p v-if="erro" style="color:red;">
          {{ erro }}
        </p>

        <table class="table">
          <thead>
            <tr>
              <th>Nome</th>
              <th>CPF</th>
              <th>Data de nascimento</th>
              <th>Email</th>
              <th>Senha</th>
              <th>Telefone</th>              
            </tr>
            <tbody>
              <tr v-for="produto in funcionarios" :key="produto.id">
              </tr>
            </tbody>
          </thead>
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


