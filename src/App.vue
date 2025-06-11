<script setup>
import 'bootstrap/dist/css/bootstrap.min.css'
import { reactive} from "vue"

const estado = reactive({
  num1: 0,
  num2: 0,
  operacao: '+',
})

function calcula() {
  const {num1, num2, operacao} = estado;
  switch (operacao) {
    case "+":
      return (num1 + num2);
    case "-":
      return num1 - num2;
    case "X":
      return num1 * num2;
    case "/":
      if (num2 != 0) {
        return num1 / num2;
      } else {
        return ("Erro (divisão por 0)")
      }
  }
    
}
</script>

<template>
  <div class="bg-dark w-50 mt-5 py-3 rounded-3 text-center mx-auto text-light">
      <h1>Calculadora</h1>
      <div id="container" class="mx-auto w-50">
        <input class="bg-secondary mx-1 rounded-2 w-25 text-center" 
          type="number" 
          v-model.number="estado.num1"
        >
        <select class="bg-secondary mx-1 rounded-2 text-center" @change="evento => estado.operacao = evento.target.value">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="X">X</option>
          <option value="/">/</option>
        </select>
        <input class="bg-secondary mx-1 rounded-2 w-25 text-center" 
          type="number"
          v-model.number="estado.num2"
        >
      </div>
      <p class="mt-3">Resultado: {{ calcula() }} </p>
  </div>
</template>