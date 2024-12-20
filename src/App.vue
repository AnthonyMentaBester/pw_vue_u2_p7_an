<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <Contador />
  <Contador />
  <!-- Si yo quiero usar el valor lo envio como atributo el props -->
  <!-- v-bind o : es para que agarre valores como java script -->
  <Contador
    encabezado="Contador Primero"
    v-bind:valor="1 + 1"
    :esVerdadero="muestra"
    :valor2="78"
  />
  <Contador
    encabezado2="Contador Segundo"
    :valor="5 + 1"
    :esVerdadero="muestraSegundo"
  />

  <!-- creare unos botones para cambiar  -->
  <button @:click="cambiar(1)">Cambiar Primero</button>
  <button @:click="cambiarSegundo(2)">Cambiar Segundo</button>
</template>

<script>
import Contador from "./components/Contador.vue";
export default {
  name: "App",
  components: {
    Contador,
  },
  data() {
    return {
      // aca le puedo decir inicia con el valor del props
      muestra: true,
      muestraSegundo: true,
    };
  },
  //no deberia ser asi aqui no van metodos
  //soo es ejemplo de como no hacerlo
  methods: {
    calcular(a, b) {
      return a + b;
    },
    cambiar(valor) {
      if (valor === 1) {
        this.muestra = !this.muestra;
      } else {
        this.muestraSegundo = !this.muestraSegundo;
      }
    },
    cambiarSegundo() {
      this.muestraSegundo = !this.muestraSegundo;
    },
  },
};
</script>.


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
