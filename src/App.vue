<script>
  export default {
    data() {
        return {
        campo1: '',
        campo2: '',
        operacao: 'soma',
        resultado: ''
        };
    },
    methods: {
        getResultado() {
        const num1 = parseFloat(this.campo1);
        const num2 = parseFloat(this.campo2);

        switch (this.operacao) {
            case 'soma':
            this.resultado = num1 + num2;
            break;
            case 'subtracao':
            this.resultado = num1 - num2;
            break;
            case 'multiplicacao':
            this.resultado = num1 * num2;
            break;
            case 'divisao':
            this.resultado = num2 !== 0 ? num1 / num2 : 'Não é possível dividir por zero';
            break;
            default:
            this.resultado = 'inválido';
        }
        }
    }
};
</script>

<template>
  <div class="container">
    <div class="calculadora">
        <h1 class="name">Calculadora</h1>
        <input v-model="campo1" class="operador" type="number" @input="getResultado">
        <select v-model="operacao" class="operador" @change="getResultado">
            <option value="soma">Soma (+)</option>
            <option value="subtracao">Subtração (-)</option>
            <option value="multiplicacao">Multiplicação (*)</option>
            <option value="divisao">Divisão (/)</option>
        </select>
        <input v-model="campo2" class="operador" type="number" @input="getResultado">
        <p class="operadores">{{ resultado }}</p>
    </div>
  </div>
</template>

<style scoped>
.calculadora {
    margin: 0 auto;
    width: 350px;
    font-size: 20px;
    display: grid;
    grid-auto-rows: minmax(50px, auto);
}
.operador {
  margin-bottom: 2px;
  background-color: #333;
  color: white;
}
.name {
  text-align: center;
}
.operadores {
    background-color: orange;
    color: white;
    padding: 10px 2px;
}
</style>

