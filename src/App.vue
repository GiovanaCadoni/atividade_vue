<script setup>
import { reactive } from 'vue';

const estado = reactive ({
  algarismo1: 0,
  algarismo2:0,
  operador: '+',
  resultado: 0,
})

function calculando(){
  const numero1 = parseFloat(estado.algarismo1)
  const numero2 = parseFloat(estado.algarismo2)

  switch (estado.operador) {
    case '+':
      estado.resultado = numero1 + numero2;
    break;
    case '-':
      estado.resultado = numero1 - numero2;
    break;
    case '*':
      estado.resultado = numero1 * numero2;
    break;
    case '/':
      estado.resultado = numero1 / numero2;
    break;

    default:
      estado.resultado = "O número não é válido";
  }
}
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <header class="p-5 mb-4 bg-light rounded-3">
      <h1 class="mt-2">Calculadora</h1>
    </header>
      </div>
      <form>
    <input @keyup="evento => {estado.algarismo1 = evento.target.value; calculando()}" type="number" placeholder="Insire os números:">
    <select @change="evento => {estado.operador = evento.target.value; calculando()}">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>
    <input @keyup="evento => {estado.algarismo2 = evento.target.value; calculando()}" type="number" placeholder="Insire os números:">
    <div class="resultado">
      {{ estado.resultado }}
    </div>
  </form>
    </div>
  </div>
</template>

<style scoped>

</style>
