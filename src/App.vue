<script setup>
import { reactive } from 'vue';

const calculo = reactive({
  num1: '',
  num2: '',
})

var resultado = 0

switch(calculo){
  case '+':
    resultado = num1 + num2
    break
    case '-':
    resultado = num1 - num2
    break
    case '*':
    resultado = num1 * num2
    break
    case '/':
    resultado = num1 / num2
    break
    default:
    alert('Digite dois valores')
    break
}




</script>

<template>
<div>
  <h3>Calculadora Vue</h3>
  <ol class="mat">
    <li>
      <input v-model.number="num1" placeholder="Digite o primeiro valor">
      <input v-model.number="num2" placeholder="Digite o segundo valor">
      <select  @change="evento => calculo.calculo = evento.target.value" name="seletor" id="seletor">
        <option value="seletor">selecionar</option>
        <option value="somar">somar</option>
        <option value="subtrair">subtrair</option>
        <option value="multi">multiplicar</option>
        <option value="dividir">dividir</option>
      </select>
      <p>Resultado:</p>
    </li>
  </ol>
</div>

</template>
<style scoped>
.mat {
    list-style: none;
  }
</style>
