<template>
  <h2> {{ tituloPersonalizado }} </h2>
  <p> {{ contador }}  <sup>2</sup> = {{ contadorCuadrado }} </p>
  <button v-on:click="cambiarValor(-1)"> - </button> <button @click="cambiarValor(1)" > + </button> 
</template>

<script>
import { computed } from '@vue/runtime-core'

export default {
    props: {
        titulo: String,
        inicio: {
            type: Number,
            required: true,
            default: 5,
            validator ( value ){
                return value >= 0
            }
        }
    },
    name:'Contador',

    data(){
        return{
            contador: this.inicio
        }
    },
    methods:{
        cambiarValor(valor){
            this.contador += valor
        }

    },
    //Almacena en caché el valor
    computed:{
        contadorCuadrado(){
            console.log('Pos aqui pasé')
            return this.contador*this.contador
        },
        tituloPersonalizado(){
            if(!this.titulo){
                return 'Contador'
            }
            return this.titulo
        }
    }

}
</script>

    

<style>

</style>