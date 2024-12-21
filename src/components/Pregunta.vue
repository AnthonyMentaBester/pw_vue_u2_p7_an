<template>
    <!-- aqui lo que quiero es visualizar la imagen del API quemada -->
  <img :src="imagen" alt="No se puede ver">
  <br>
  <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" name="" id="">

  <p>Recuerda que cuando finalices tu pregunta debes poner ? </p>

  <h1>{{pregunta}}</h1>
  <h2>{{respuesta}}</h2>
</template>

<script>
export default {
    data() {
        return {
            pregunta: 'Hola Mundo',
            respuesta: null,
            imagen: 'https://yesno.wtf/assets/yes/14-b57c6dc03aa15a4b18f53eb50d6197ee.gif',
        }
    },
    watch: {
        //declarar un watch estandar
        pregunta(value, oldValue) {
            //para usar el watch el atributo lo pongo con el mismo nombre como si fuera un metodo
            console.log(value);
            console.log(oldValue);
            if(value.includes('?')){
                //vamos a programar la llamada al API
                //para obtener el SI o EL NO, y la imagen
                console.log('Aqui llamos al API');
                this.obtenerRespuestaAPI();
            }
        }
    },
    methods: {
        //voy a tener un metodo llame al API
        //RECORDAR PORNERLO EL ASYNC
        async obtenerRespuestaAPI(){
            //aqui recibe el elemento del API
            //es necesario poner const y el await
            const data = await fetch('https://yesno.wtf/api').then(resp=>resp.json());
            this.respuesta = data.answer;
            this.imagen = data.image;  
            console.log(data);
        },
        async fachada(){
            //para llamar un asyncrono debo usar el await
            await this.obtenerRespuestaAPI();
        }
    }
}
</script>

<style>

</style>