<script setup>
import { reactive } from 'vue';

const estado = reactive({
  primaryNumber: '',
  secondNumber: '',
  operations: {
    add: (a, b) => a + b,
    subtract: (a, b) => a - b,
    multiply: (a, b) => a * b,
    divide: (a, b) => (b !== 0 ? a / b : "The result doesn't exist"),
  },
  result: '0',
  mathOperation: 'add',
})

const calculateResult = () => {
  const { primaryNumber, secondNumber, mathOperation } = estado;
  estado.result = estado.operations[mathOperation](parseFloat(primaryNumber), parseFloat(secondNumber));
}
</script>

<template>

  <body>
    <div class="container">
      <div class="calculator">
        <input v-model="estado.primaryNumber" @input="calculateResult" type="number"
          placeholder="Digite o primeiro número">

        <select v-model="estado.mathOperation" @change="calculateResult">
          <option value="add">+</option>
          <option value="subtract">-</option>
          <option value="multiply">*</option>
          <option value="divide">/</option>
        </select>

        <input v-model="estado.secondNumber" @input="calculateResult" type="number"
          placeholder="Digite o segundo número">

        <p class="result">Resultado: {{ estado.result }}</p>
      </div>
    </div>
  </body>
</template>

<style scoped>
body {
  background-color: #343a40;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  margin: 0;
}

.container {
  width: 100%;
  max-width: 400px;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0px 8px 10px rgba(0, 0, 0, 0.1);
}

.calculator input,
.calculator select {
  margin-bottom: 10px;
  padding: 8px;
  border: 1px solid #ccc;
}

.calculator input,
.calculator select,
.calculator p {
  border-radius: 4px;
  width: 100%;
}

.calculator p {
  padding: 8px 16px;
  margin: 16px 0 0 0;
  border: none;
  font-size: 18px;
  color: #919191;
  border: 2px solid #0db654;
}
</style>