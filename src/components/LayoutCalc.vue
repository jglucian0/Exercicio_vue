<script setup>
const props = defineProps(['primaryNumber', 'secondNumber', 'calculateResult', 'mathOperation', 'result'])
</script>

<template>
  <body>
    <div class="container">
      <div class="calculator">
        <input v-model="props.primaryNumber" @input="props.calculateResult" type="number"
          placeholder="Digite o primeiro número">

        <select v-model="props.mathOperation" @change="props.calculateResult">
          <option value="add">+</option>
          <option value="subtract">-</option>
          <option value="multiply">*</option>
          <option value="divide">/</option>
        </select>

        <input v-model="props.secondNumber" @input="props.calculateResult" type="number"
          placeholder="Digite o segundo número">

        <p class="result">Resultado: {{ props.result }}</p>
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