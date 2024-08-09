<script setup>
import { reactive } from 'vue';

const estado = reactive({
    primeiroNumero: '',
    segundoNumero: '',
    operacoes: {
        adicao: (a, b) => a + b,
        subtracao: (a, b) => a - b,
        multiplicacao: (a, b) => a * b,
        divisao: (a, b) => (b !== 0 ? a / b : 'Divisão por zero'),
    },
    resultado: 0,
});

const resultado = () => {
    const { primeiroNumero, segundoNumero, operacaoMatematica } = estado;
    estado.resultado = estado.operacoes[operacaoMatematica](parseFloat(primeiroNumero), parseFloat(segundoNumero));
};
</script>

<template>
    <div class="container ">
      <div class="header">
        <h1>Calculadora Aritmética Simples</h1>
      </div>
    </div>
    <div class="container ">
      <input type="text" v-model="estado.primeiroNumero" @input="resultado" />
      <input type="text" v-model="estado.segundoNumero" @input="resultado" />

      <select v-model="estado.operacaoMatematica" @change="resultado">
        <option value="adicao">Adição +</option>
          <option value="subtracao">Subtração -</option>
          <option value="multiplicacao">Multiplicação *</option>
          <option value="divisao">Divisão /</option>
      </select>

      <p>Resultado: {{ estado.resultado }}</p>

    </div>
</template>

<style scoped>
.container {
  max-width: 320px;
  margin: 12px auto;
  padding: 20px;
  background-color: #7c0a0a;
  border-radius: 5px;
  color: #f76505;
}

h1 {
  font-size: 18px;
  text-align: center;
}

input {
  margin: 10px 0;
  padding: 10px;
  width: 300px;
  border: 1px solid #f76505;
  border-radius: 5px;
  display: flex;
  align-items: center;
  text-align: center;
  background-color: #6b6868;
  color: #fff;

}

select {
  margin: 10px 0;
  padding: 8px;
  width: 320px;
  border: 1px solid #f76505;
  border-radius: 3px;
  display: flex;
  align-items: center;
  text-align: center;
  font-size: 16px;
  background-color: #6b6868;
  color: #fff;

}

option {
  font-size: 16px;
  background-color: #f76505;
  color: #7c0a0a;;
}

p {
  font-size: 16px;
  margin-top: 16px;
  text-align: center;
}
</style>