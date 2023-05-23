<script setup>
import { computed, reactive } from 'vue'

const nome = 'Calculadora Aritimetica'
const estado = reactive({
  resultado: 0,
  n1: 0,
  n2: 0,
  soma: 'Soma',
  sub: 'Subtracao',
  mult: 'Multiplicacao',
  div: 'Divisao'
})
const operacao = {
  soma: true,
  sub: false,
  mult: false,
  div: false
}
</script>

<template>
  <h1>{{ nome }}</h1>
  <input
    @keyup="(evento) => (estado.n1 = evento.target.value)"
    type="number"
    placeholder="Primeiro numero"
  /><br />
  <input
    @keyup="(evento) => (estado.n2 = evento.target.value)"
    type="number"
    placeholder="Segundo numero"
  />
  <select name="operacoes" v-model="operacao">
    <option value="soma">{{ estado.soma }}</option>
    <option value="sub">{{ estado.sub }}</option>
    <option value="mult">{{ estado.mult }}</option>
    <option value="div">{{ estado.div }}</option>
  </select>
  <br />
  Resultados:
  <p v-if="operacao == 'soma'">{{ number(estado.n1) + number(estado.n2) }}</p>
  <p v-else-if="operacao == 'sub'">{{ estado.n1 - estado.n2 }}</p>
  <p v-else-if="operacao == 'mult'">{{ estado.n1 * estado.n2 }}</p>
  <p v-else-if="operacao == 'div'">{{ estado.n1 / estado.n2 }}</p>
  Primeiro valor escolhido: {{ estado.n1 }} <br />Segundo valor escolhido:
  {{ estado.n2 }} <br />
</template>

<style scoped>
* {
  max-width: 960px;
}
h1 {
  text-align: center;
  background: rgb(248, 195, 98);
}
</style>
