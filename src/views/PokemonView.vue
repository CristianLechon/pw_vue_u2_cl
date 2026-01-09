<template>
  <div>
    <h1>{{ mensaje }}</h1>
    <PokemonImagen :pokemonId="pokemonGanador" />
    <PokemonOpciones @seleccionado="evaluarGanador($event)" :listaPokemons="pokemonArr" />
  </div>
</template>

<script>
import PokemonOpciones from "@/components/PokemonOpciones.vue";
import PokemonImagen from "@/components/PokemonImagen.vue";
import {
  obtenerVectorPokemonFacade,
  obtenerAleatorioFachada,
} from "../clients/PokemonClient.js";
export default {
  components: {
    PokemonImagen,
    PokemonOpciones,
  },
  data() {
    return {
      pokemonArr: [],
      pokemonGanador: null,
      mensaje: null
    };
  },
  // para que se carge cuando se ejecute
  mounted() {
    console.log("Componente montado");
    this.iniciarJuego();
  },
  methods: {
    async iniciarJuego() {
      this.pokemonArr = await obtenerVectorPokemonFacade();

      const idAleatorio = obtenerAleatorioFachada(0, 3);
      this.pokemonGanador = this.pokemonArr[idAleatorio].id;
      const n = this.pokemonArr[idAleatorio].nombre;
      console.log(n);

    },
    evaluarGanador(idGanador){
      console.log('valor recibido desde padre');
      console.log(idGanador);
      if (idGanador === this.pokemonGanador) {
        console.log('Ganador');
        this.mensaje = 'Haz selecionado el pokemon correcto';
      } else {
        this.mensaje = 'Haz selecionado el pokemon incorrecto';
        console.log('Perdedor');
      }
    }
  },
};
</script>

<style scoped>
  h1{
    position: relative;
    left: 36%;
  }
</style>