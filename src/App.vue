<script setup>
import { reactive } from "vue";
import { props } from "vue";

const props = defineProps(["valorNumero1", "valorNumero2", "trocarFiltro"]);

const estado = reactive({
  filtro: "multiplicacao",
  numero1: 0,
  numero2: 0,
});

const multiplicacao = ({ numero1, numero2 } = estado) => {
  return numero1 * numero2;
};

const adicao = ({ numero1, numero2 } = estado) => {
  return Number(numero1 + numero2);
};

const subtracao = ({ numero1, numero2 } = estado) => {
  return numero1 - numero2;
};

const divisao = ({ numero1, numero2 } = estado) => {
  return numero1 / numero2;
};

const matematica = () => {
  const { numero1, numero2, filtro } = estado;

  if ((numero1, numero2)) {
    switch (filtro) {
      case "multiplicacao":
        return multiplicacao();
      case "adicao":
        return adicao();
      case "subtracao":
        return subtracao();
      case "divisao":
        return divisao();
    }
  }
};

</script>


<template>
  <header class="mt-4 text-center">
    <h1>Operações Matemáticas</h1>
    <p>Digite os Numeros</p>
  </header>
  <form>
    <div class="row d-flex align-items-center">
      <div class="col gap-2 d-flex">
        <input @keyup="props.valorNumero1" :valor-numero1="(event) => (estado.numero1 = Number(event.target.value))" class="form-control" type="number" />
        <input @keyup="props.valorNumero2" :valor-numero2="(event) => (estado.numero2 = Number(event.target.value))" class="form-control" type="number" />
      </div>
      <div class="col">
        <select @change="props.trocarFiltro" :trocar-filtro="(event) => (estado.filtro = event.target.value)" class="form-control text-center">
          <option value="multiplicacao">Multiplicação</option>
          <option value="adicao">Adição</option>
          <option value="subtracao">Subtração</option>
          <option value="divisao">Divisão</option>
        </select>
      </div>
    </div>
  </form>
</template>

<style scoped>

</style>
