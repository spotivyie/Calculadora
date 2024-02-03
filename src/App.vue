<script>
  export default {
  data() {
    return {
      valor: '',
      anterior: null,
      operador: null,
      operadorClicado: false,
    };
  },
  methods: {
    limpar() {
      this.valor = '';
    },
    sinal() {
      this.valor = this.valor.charAt(0) === '-'
        ? this.valor.slice(1)
        : `-${this.valor}`;
    },
    porcentagem() {
      this.valor = `${parseFloat(this.valor) / 100}`;
    },
    numeros(numero) {
      if (this.operadorClicado) {
        this.valor = '';
        this.operadorClicado = false;
      }
      this.valor = `${this.valor}${numero}`;
    },
    ponto() {
      if (this.valor.indexOf('.') === -1) {
        this.numeros('.');
      }
    },
    setarValor() {
      this.anterior = this.valor;
      this.operadorClicado = true;
    },
    dividir() {
      this.operador = (n1, n2) => n1 / n2;
      this.setarValor();
    },
    multiplicar() {
      this.operador = (n1, n2) => n1 * n2;
      this.setarValor();
    },
    diminuir() {
      this.operador = (n1, n2) => n1 - n2;
      this.setarValor();
    },
    somar() {
      this.operador = (n1, n2) => n1 + n2;
      this.setarValor();
    },
    resultado() {
      this.valor = `${this.operador(
        parseFloat(this.anterior),
        parseFloat(this.valor),
      )}`;
      this.anterior = null;
    },
  },
};
</script>

<template>
  <div class="all">
    <h1 class="name">Calculadora</h1>
    <div class="calculadora">
        <div class="display">{{valor || '0'}}</div>
        <div v-on:click="limpar" class="botao">C</div>
        <div v-on:click="sinal" class="botao">+/-</div>
        <div v-on:click="porcentagem" class="botao">%</div>
        <div v-on:click="dividir" class="botao">÷</div>
        <div v-on:click="numeros('7')" class="botao">7</div>
        <div v-on:click="numeros('8')" class="botao">8</div>
        <div v-on:click="numeros('9')" class="botao">9</div>
        <div v-on:click="multiplicar" class="botao">x</div>
        <div v-on:click="numeros('4')" class="botao">4</div>
        <div v-on:click="numeros('5')" class="botao">5</div>
        <div v-on:click="numeros('6')" class="botao">6</div>
        <div v-on:click="diminuir" class="botao">-</div>
        <div v-on:click="numeros('1')" class="botao">1</div>
        <div v-on:click="numeros('2')" class="botao">2</div>
        <div v-on:click="numeros('3')" class="botao">3</div>
        <div v-on:click="somar" class="botao">+</div>
        <div v-on:click="numeros('0')" class="botao zero">0</div>
        <div v-on:click="ponto" class="botao">.</div>
        <div v-on:click="resultado" class="botao operadores">=</div>
    </div>
  </div>
</template>

<style scoped>
.all{
  font-family: Arial, Helvetica, sans-serif;
  font-weight: lighter;
}
.name{
  text-align: center;
  font-weight: lighter;
}
.calculadora {
  margin: 0 auto;
  width: 280px;
  font-size: 34px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  background-color: #c9c7c779;
  padding: 20px 6px;
  border-radius: 6px;
}

.display {
  background-color: #333;
  color: white;
  text-align: end;
  grid-column: 1 / 5;
  padding: 6px 34px;
  border-radius: 6px;
  margin: 2px;
  margin-bottom: 20px;
}

.zero {
  grid-column: 1 / 3;
}

.botao {
  background-color: #f2f2f2;
  text-align: center;
  border: 1px solid #999;
  padding: 6px 0;
  margin: 2px;
  border-radius: 6px;
  cursor: pointer;
}
.operadores {
  background-color: rgba(0, 47, 255, 0.733);
  color: white;
}
</style>