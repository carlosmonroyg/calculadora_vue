<template>
  <div id="app">
  
  <Calculadora/>
  <Calculator/>
  </div>
</template>

<script>
import Calculadora from "./components/Calculadora.vue";
import Calculator from "./components/Calculator.vue";



export default {
  name: "App",
  components: {
    Calculadora,
    Calculator,
  
},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
