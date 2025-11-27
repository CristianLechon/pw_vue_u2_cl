<template>
  <div>
    <!-- Cada componete tiene su estado -->
    <!-- <Contador tit="Contador 1" v-bind:inicio="4+4"/> -->
    <Contador tit="Contador 1" v-bind:inicio="20" :mostrar="true"/>
    <Contador tit="Contador 2" :inicio="4" :mostrar="false"/>
    <!-- <Contador /> -->
    <!-- <Contador /> -->
  </div>
</template>

<script>
import Contador from "../components/Contador.vue";
export default {
  components: {
    Contador,
  },
};
</script>

<style>
</style>