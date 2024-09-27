<template>
  <body>
    <div class="Calculadora">
    <div class="resutaldo">0</div>
    <div class = "btn funcion">C</div>
    <div class = "btn funcion">+/-</div>
    <div class = "btn funcion">%</div>
    <div class = "btn Operator">÷</div>
    <div class = "btn">7</div>
    <div class = "btn">8</div>
    <div class = "btn">9</div>
    <div class = "btn Operator">x</div>
    <div class = "btn">4</div>
    <div class = "btn">5</div>
    <div class = "btn">6</div>
    <div class = "btn Operator">-</div>
    <div class = "btn">1</div>
    <div class = "btn">2</div>
    <div class = "btn">3</div>
    <div class = "btn Operator">+</div>
    <div class = "btn cero">0</div>
    <div class = "btn">.</div>
    <div class = "btn Operator">=</div>


  </div>


  </body>
  
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      resultado: 0,
    };
  },

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
