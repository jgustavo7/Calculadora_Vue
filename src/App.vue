<script setup>
import { reactive } from "vue";

const estado = reactive({
  filtro: "multiplicacao",
  numero1: 0,
  numero2: 0,
});

const multiplicacao = () => {
  return Number(estado.numero1 * estado.numero2);
};

const adicao = () => {
  return Number(estado.numero1 + estado.numero2);
};

const subtracao = () => {
  return Number(estado.numero1 - estado.numero2);
};

const divisao = () => {
  return Number(estado.numero1 / estado.numero2);
};

const resultado = () => {
  const { numero1, numero2, filtro, } = estado;

  if (numero1 !== null && numero2 !== null) {
    switch (filtro) {
      case "multiplicacao":        
        return multiplicacao();
        case "adicao":        
        return adicao();
        case "subtracao":        
        return subtracao();
        case "divisao":        
        return divisao();
        default:
          return null;
    }
  }
}

</script>


<template>
<div id="app" data-v-app>
<div class="container">
<header class="mt-4 text-center">
  <h1 class="mb-5">Operações</h1>
</header>
<form>
  <div class="row d-flex align-items-center">
    <div class="col gap-2 d-flex">
      <input @input="(event) => (estado.numero1 = Number(event.target.value))" class="form-control" type="number" placeholder="Digite um numero">
      <input @input="(event) => (estado.numero2 = Number(event.target.value))" class="form-control" type="number" placeholder="Digite um numero">
    </div>
    <div class="col">
      <select @change="(event) => (estado.filtro = event.target.value)" class="form-control text-center">
        <option value="multiplicacao">Multiplicação</option>
        <option value="adicao">Adição</option>
        <option value="subtracao">Subtração</option>
        <option value="divisao">Divisão</option>
      </select>
    </div>
  </div>
</form>
<p class="mt-4 fs-2">Resultado: {{ resultado() }}</p>
</div>
</div>
</template>

<style scoped>

</style>
