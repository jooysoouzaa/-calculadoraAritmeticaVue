<script setup>
import { ref, computed } from 'vue';

const number1 = ref(null);
const number2 = ref(null);
const operation = ref('add');

const result = computed(() => {
  if (number1.value === null || number2.value === null) return '';

  switch (operation.value) {
    case 'add':
      return number1.value + number2.value;
    case 'subtract':
      return number1.value - number2.value;
    case 'multiply':
      return number1.value * number2.value;
    case 'divide':
      return number2.value !== 0 ? number1.value / number2.value : 'Erro: Divisão por zero';
    default:
      return 0;
  }
});
</script>


<template>
  <div class="container">
    <div id="app">
      <h1>Calculadora</h1>
      <div class="operador">
        <label>Escolha o operador</label>
        <select v-model="operation">
          <option value="add">Adição</option>
          <option value="subtract">Subtração</option>
          <option value="multiply">Multiplicação</option>
          <option value="divide">Divisão</option>
        </select>
      </div>
      <div class="numbers">
        <div>
          <input type="number" v-model.number="number1" placeholder="Digite um número" />
        </div>
        <div>
          <input type="number" v-model.number="number2" placeholder="Digite um número" />
        </div>
      </div>
      <div>
        <h2>Resultado: {{ result }}</h2>
      </div>
    </div>
  </div>
</template>


<style scoped>
.container {
  max-width: 100%;
  height: 100vh;
  padding: 0 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}

#app {
  width: 100%;
  max-width: 400px;
  background-color: #1D8A994d;
  color: #ffffff;
  padding: 40px;
  border-radius: 8px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

h1 {
  font-size: 2.2em;
}

.numbers {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}

label {
  font-size: 1.2em;
  margin-right: 10px;
}

input {
  font-size: 1em;
  width: 85%;
  margin: 0 auto;
}

.operador {
  padding: 12px 0;
  margin: 0 auto;
}

select {
  font-size: 1em;
  width: 100%;
  margin-top: 8px
}

input,
select {
  background-color: #00000054;
  color: #ffffff;
  border-radius: 6px;
  margin-bottom: 10px;
  padding: 12px;
  border: none;
}

select:focus {
  color: #ffffff;
  outline: none;
}

input::placeholder {
  color: #9b9b9b;
}

input:focus {
  color: #ffffff;
  outline: none;
}

@media only screen and (max-width: 767px) {
  #app {
    padding: 20px;
  }

}

@media only screen and (max-width: 375px) {

  input {
    width: 80%;
  }
}
</style>
