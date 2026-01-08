<template>
  <div>
    <PokemonImagen :pokemonId="23"/>
    <PokemonOpciones />
  </div>
</template>

<script>
import PokemonOpciones from "@/components/PokemonOpciones.vue";
import PokemonImagen from "@/components/PokemonImagen.vue";
export default {
  components: {
    PokemonImagen,
    PokemonOpciones,
  },
};
</script>

<style>
</style>