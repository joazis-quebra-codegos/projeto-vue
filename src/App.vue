<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col">
          <h1>Ola mundo projeto vue</h1>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur necessitatibus, hic ad aliquam iusto quam neque incidunt quia atque, aliquid ex enim facilis mollitia consequuntur molestias, dicta eveniet error ipsum!</p>
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


