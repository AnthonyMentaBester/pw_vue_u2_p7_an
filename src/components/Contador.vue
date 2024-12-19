<!-- -->
<template>
  <h2>{{titulo}}</h2>
  <!-- asi debo llamar a los methods -->
  <p>{{numero}} <sup>2</sup> = {{ calcularCuadrado() }}</p>
  <!-- debo ver como debo llamar alas propiedades computadas -->
  <p>{{numero}} <sup>2</sup> = {{ calcularCuadradoComputado }}</p>
  <p>{{numero}} <sup>2</sup> = {{ calcularCuadradoComputado }}</p>
  <p>{{numero}} <sup>2</sup> = {{ calcularCuadradoComputado }}</p>
  <p>{{numero}} <sup>2</sup> = {{ calcularCuadradoComputado }}</p> 
  <div>
    <!-- asi debo llamar a los methods con la directiva v-on o el @ -->
    <button v-on:click="incrementar()">+1</button>
    <button @click="decrementar()">-1</button>
  </div>
</template>

<script>
export default {
    data() {
        return {
            numero: 10,
            titulo: 'Contador'
        }
    },
    methods: {
        calcularCuadrado() {
            console.log('Entro a calcular cuadrado');
            return this.numero * this.numero;
        },
        incrementar() {
            this.numero++;
        },
        decrementar() {
            this.numero--;
        }
    },
    computed: {
        calcularCuadradoComputado() {
            console.log('Entro a calcular cuadrado computado');
            return this.numero * this.numero;
        }
    }
};
</script>

<style>
button {
    background: #50c48f;
    border-radius: 5px;
    border: 1px solid white;
    color: white;
    cursor: pointer;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
    padding: 10px 20px;
    font-size: 16px;
    margin: 10px;
}
button:hover {
    background: #4bbf8c;
}

</style>