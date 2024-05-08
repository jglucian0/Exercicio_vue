<script setup>
import { reactive } from 'vue';
import LayoutCalc from './components/LayoutCalc.vue';

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
};
</script>

<template>
  <LayoutCalc
  :result="estado.result"
  :primary-number="estado.primaryNumber"
  :math-operation="estado.mathOperation"
  :second-number="estado.secondNumber"
  />
</template>

<style scoped></style>
