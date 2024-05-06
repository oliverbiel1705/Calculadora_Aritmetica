<script setup>
import { reactive } from 'vue';

const calc = reactive({
  numero1: '0',
  numero2: '0',
  operacao: 'somar',
})

function operacaoResultado(){
  const {operacao} = calc

  switch(operacao){
    case 'subtrair': return parseInt(calc.numero1) - parseInt(calc.numero2)
    case 'multiplicar': return parseInt(calc.numero1) * parseInt(calc.numero2)
    case 'dividir': return parseInt(calc.numero1) / parseInt(calc.numero2)

    default: return parseInt(calc.numero1) + parseInt(calc.numero2)
  }
}

</script>

<template>
  <div class="container">
    <h1 class="text-center mt-3 mb-5">Calculadora Aritmética</h1>
    <div class="row">
      <input type="number" class="form-control col text-center" placeholder="Número 1" @keyup="evento => calc.numero1 = evento.target.value">
      <select class="form-control col-1 col-md ms-2 me-2 text-center" @change="evento => calc.operacao = evento.target.value">
        <option value="somar">+</option>
        <option value="subtrair">-</option>
        <option value="multiplicar">x</option>
        <option value="dividir">÷</option>
      </select>
      <input type="number" class="form-control col text-center" placeholder="Número 2" @keyup="evento => calc.numero2 = evento.target.value">
    </div>

    <div class="mt-5 text-center">
      <h2>{{ operacaoResultado() }}</h2>
    </div>
  </div>
</template>

<style scoped>
input[type="number"]::-webkit-outer-spin-button,
input[type="number"]::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
}

</style>
