<script setup>
import { reactive, ref } from 'vue';

const calculo = reactive({
  num1: '',
  num2: '',
})

const resultado = ref(0);
const operacao = ref('');

function calcular() {
  const num1 = parseFloat(calculo.num1);
  const num2 = parseFloat(calculo.num2);

  if (isNaN(num1) || isNaN(num2)) {
    alert('Digite dois valores válidos');
    return;
  }

  switch (operacao.value) {
    case 'somar':
      resultado.value = num1 + num2;
      break;
    case 'subtrair':
      resultado.value = num1 - num2;
      break;
    case 'multi':
      resultado.value = num1 * num2;
      break;
    case 'dividir':
      if (num2 === 0) {
        alert('Não é possível dividir por zero');
        return;
      }
      resultado.value = num1 / num2;
      break;
    default:
      alert('Selecione uma operação');
      break;
  }
}
</script>

<template>
  <div class="container">
    <header class="titulo">
      <h3>Calculadora VUE</h3>
      <img src="./img/calc.png" alt="calculadora">
    </header>
    <ol class="mat">
      <li class="lista">
        <input v-model.number="calculo.num1" placeholder="Digite o primeiro valor">
        <input v-model.number="calculo.num2" placeholder="Digite o segundo valor">
        <select v-model="operacao" name="seletor" id="seletor">
          <option value="">selecionar</option>
          <option value="somar">somar</option>
          <option value="subtrair">subtrair</option>
          <option value="multi">multiplicar</option>
          <option value="dividir">dividir</option>
        </select>
        <button @click="calcular">Calcular</button>
        <p class="result">Resultado: {{ resultado }}</p>
      </li>
    </ol>
  </div>
</template>


<style scoped>
.container {
  max-width: 960px;
  width: 100%;
  margin: 0 auto;
}
.titulo {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(73, 240, 204);
}

img {
  max-width: 40px;
  position: relative;
  left: 2%;
}
.mat {
  list-style: none;
  display: flex;
  justify-content: center;
  align-items: center;
}
.result {
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration:overline;
  font-weight: bold;
}
</style>
