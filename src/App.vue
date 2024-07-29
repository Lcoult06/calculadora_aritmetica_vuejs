<script setup>
import { ref, watch } from 'vue';

const num1 = ref(0);
const num2 = ref(0);
const operacao = ref('+');
const resultado = ref(0);

watch([num1, num2, operacao], () => {
  calcular();
});

function calcular() {
  switch (operacao.value) {
    case '+':
      resultado.value = num1.value + num2.value;
      break;
    case '-':
      resultado.value = num1.value - num2.value;
      break;
    case '*':
      resultado.value = num1.value * num2.value;
      break;
    case '/':
      if (num2.value !== 0) {
        resultado.value = num1.value / num2.value;
      } else {
        resultado.value = 'Erro: divisão por zero';
      }
      break;
  }
}
</script>

<template>
  <div class="container" id="calculadora">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>Calculadora Aritmética</h1>
    </header>
    <form>
      <div class="row">
        <div class="col md-2">
          <input  type="number" v-model.number="num1" placeholder="Digite um valor númerico" class="form-control">
        </div>
        <div class="col md-2">
          <select v-model="operacao" class="form-control">
            <option value="+">adição</option>
            <option value="-">subtração</option>
            <option value="*">multiplicação</option>
            <option value="/">divisão</option>
          </select>
        </div>
        <div class="col md-2">
          <input  type="number" v-model.number="num2" placeholder="Digite um valor númerico" class="form-control">
        </div>
      </div>
    </form>
    <div class="row mb-4 mt-4 ">
      <p>O resultado da operação é: {{ resultado }} </p>
    </div>
  </div>

</template>

<style scoped>
  .container {
    max-width: 400px;
    margin: 40px auto;
    padding: 20px;
    background-color: #57b5eb;
    border-radius: 10px;
  }

  header {
    color: blue;
  }

  p {
    font-weight: bold;
  }
</style>
