<template>
<body>
  <div class="Calculadora">
  <div class="resutaldo">{{actual || '0'}}</div>
  <div @click="clear" class = "btn funcion">C</div>
  <div @click="signo" class = "btn funcion">+/-</div>
  <div @click="porcentaje" class = "btn funcion">%</div>
  <div @click="division" class = "btn Operator">÷</div>
  <div @click="append('7')" class = "btn">7</div>
  <div @click="append('8')" class = "btn">8</div>
  <div @click="append('9')" class = "btn">9</div>
  <div @click="multiplicacion" class = "btn Operator">x</div>
  <div @click="append('4')" class = "btn">4</div>
  <div @click="append('5')" class = "btn">5</div>
  <div @click="append('6')" class = "btn">6</div>
  <div @click="resta" class = "btn Operator">-</div>
  <div @click="append('1')" class = "btn">1</div>
  <div @click="append('2')" class = "btn">2</div>
  <div @click="append('3')" class = "btn">3</div>
  <div @click="suma" class = "btn Operator">+</div>
  <div @click="append('0')" class = "btn cero">0</div>
  <div @click= "punto" class = "btn">.</div>
  <div @click="igual" class = "btn Operator">=</div>
  </div>
  </body>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      anterior: null,
      actual: '',
      operador: null,
      operadorClickeado: false,
    };
  },
  methods: {
    clear() {
      this.actual = '';
      this.anterior = null;
      this.operador = null;
      this.operadorClickeado = false;
    },
    signo() {
      this.actual = this.actual.charAt(0) === '-' ? this.actual.slice(1) : `-${this.actual}`; 
    },
    porcentaje() {
      this.actual = `${parseFloat(this.actual) / 100}`;
    },
    append(number) {
      if (this.operadorClickeado) {
        this.actual = '';
        this.operadorClickeado = false;
      }
      this.actual = `${this.actual}${number}`;
    },
    punto() {
      if (this.actual.indexOf('.') === -1) {
        this.actual += '.';
      }
    },
    setOperador(operacion) {
      if (this.anterior !== null) {
        this.igual();
      }
      this.operador = operacion;
      this.anterior = this.actual;
      this.operadorClickeado = true;
    },
    division() {
      this.setOperador((a, b) => a / b);
    },
    multiplicacion() {
      this.setOperador((a, b) => a * b);
    },
    resta() {
      this.setOperador((a, b) => a - b);
    },
    suma() {
      this.setOperador((a, b) => a + b);
    },
    igual() {
      if (this.operador && this.anterior !== null) {
    this.actual = `${this.operador(parseFloat(this.anterior), parseFloat(this.actual))}`;
    this.anterior = null;
    this.operadorClickeado = true;
  }
}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.body{
  background-color: black;
}
.Calculadora{
  margin: 0 auto;
  Width: 400px;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows:minmax(50px, auto);
  text-align: center;
  justify-content: center;
  align-items: center;

}

.resutaldo{
  grid-column: 1 / 5;
  background: #000;
  align-items: end;
  text-align: right;
  padding-right: 20px;
  justify-content: flex-end;
  color:white;
  border-radius: 12px;
}

.cero{
  grid-column: 1 / 3; /* Hace que el botón del "0" ocupe las dos primeras columnas */
}

.btn {
  background-color: #313131;
  border: 1px solid #999;
  border-radius: 20px; /* Ajusta el valor según sea necesario */
  color: white;

}

.Operator {
  background-color: #f49a07;
  border: 1px solid #999;
  border-radius: 20px; /* Ajusta el valor según sea necesario */
  color: white;

}

.funcion {
  background-color: #a0a0a0;
  border: 1px solid #999;
  border-radius: 20px; /* Ajusta el valor según sea necesario */
  color: #010101;

}

</style>
