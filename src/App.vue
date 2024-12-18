<script setup>
  import { reactive } from 'vue';
  
  const estado = reactive({
    operador: 'somar',
    numA: '0',
    numB: '0',
  })

  function somar(a,b) {
    return a + b
  }

  function subtrair(a, b) {
    return a - b
  }

  function multiplicar(a, b) {
    return a * b
  }

  function calculaValores() {
    const operacao = estado.operador
    const numeroA = Number(estado.numA)
    const numeroB = Number(estado.numB)

    switch (operacao) {
      case 'multiplicar':
        return multiplicar(numeroA,numeroB)
      case 'subtrair':
        return subtrair(numeroA, numeroB)
      default:
        return somar(numeroA, numeroB)
    }
  }
</script>

<template>
  <div class="container">
    <header>
      <h1>Calculadora</h1>
      <p>Digite os valores que serão calculados nos campos abaixo</p>
    </header>
    <div class="calculo">
      <input @keyup="evento => estado.numA = evento.target.value" type="number" >
    <select class="operadores" @change="evento => estado.operador = evento.target.value">
      <option value="somar">+</option>
      <option value="subtrair">-</option>
      <option value="multiplicar">*</option>
    </select>
    <input @keyup="evento => estado.numB = evento.target.value" type="number">
    <span style="margin-left: 8px;">=</span>
    <span class="resultado">{{ calculaValores() }}</span>
    </div>
  </div>
</template>

<style scoped>
  body {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  header {
    padding: 24px;
  }

  p {
    font-size: 20px;
  }

  input {
    padding: 8px;
    font-size: 18px;
  }

  .container {
    max-width: 720px;
    width: 100%;
    margin: 0 auto;
  }

  select {
    padding: 4px;
    font-size: 18px;
  }

  .operadores {
    margin-left: 12px;
    margin-right: 12px;
  }

  .calculo {
    margin-top: 18px;
  }

  .resultado {
    margin-left: 8px;
    font-weight: bold;
    font-size: 24px;
  }
</style>
