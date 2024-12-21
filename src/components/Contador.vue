<!-- -->
<template>
  <h2>{{titulo}}</h2>
  <!-- asi debo usar el props  -->
  <h2>{{encabezado}}</h2>
  <!-- asi debo usar el props de un objeto valor 2  -->
  <h2>{{encabezado}} : {{valor2}}</h2>
  <!-- valido que no tenga la letra a  -->
  <h2>{{encabezado2}} : {{valor2}}</h2>
  <p>{{valor}} <sup>2</sup> = {{ calcularCuadradoComputado }}</p>
  <!-- asi debo llamar a los methods -->
  <p>{{numero}} <sup>2</sup> = {{ calcularCuadrado() }}</p>
  <!-- debo ver como debo llamar alas propiedades computadas -->
  <p>{{numero}} <sup>2</sup> = {{ calcularCuadradoComputado }}</p>
  <p>{{numero}} <sup>2</sup> = {{ calcularCuadradoComputado }}</p>
  <div>
    <!-- asi debo llamar a los methods con la directiva v-on o el @ -->
    <button v-on:click="incrementar()">+1</button>
    <button @:click="decrementar()">-1</button>
  </div>
  <div v-if="esVerdadero">
    <!-- quiero mostrar el mensaje desde el padre -->
    <h1 >FELIZ NAVIDAD</h1>
  </div>

</template>

<script>
export default {
    data() {
        return {
            // aca le puedo decir inicia con el valor del props
            numero: this.valor,
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
    },
    /*asi debodeclarar los porp ejemplo de cambiar titulos pero igual formuulario*/
    //primera forma
    props:['encabezado','valor'],
    //se declaran de 3 formas
    //segunda forma
    props:{
        encabezado: String,
        encabezado2:{
            type: String,
            required: false,
            //debo validar que no tenga letra a
            validator(value){
                return !value.includes('a');
            }
        },
        valor: Number,
        valor2:{
            type: Number,
            required: false,
            //el props manda este valor si no se especifica uno
            default: 77,
            //declaro un validador
            validator(value){
                //programo mi validacion bajo mi criterio retorno
                //true es es valido para mi 
                //false no es valido para mi
                return value <= 77;

            }
        },
        //obligo a ser un props obligatorio
        esVerdadero: {
            type: Boolean,
            required: true
        },
        arreglo: Array,
        fecha: Date,
        objetoPersona: Object,
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