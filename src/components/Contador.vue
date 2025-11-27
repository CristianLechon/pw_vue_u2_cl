<template>
  <div>
    <h1>{{ tit }}</h1>
    <p>{{ numero }} <sup>2</sup>={{ calcularCuadrados }}</p>
    <p>{{ numero }} <sup>2</sup>={{ calcularCuadrados }}</p>
    <p>{{ numero }} <sup>2</sup>={{ calcularCuadrados }}</p>
    <p>{{ numero }} <sup>3</sup>={{ calcularCubo }}</p>
    <p>{{ numero }} <sup>3</sup>={{ obtenerCubo() }}</p>
    <div>
      <!-- directiva empieza con v- -->
      <button @:click="incrementar()">+1</button>
      <button v-on:click="decrementar()">-1</button>
      <button v-if="mostrar">prueba</button>
    </div>
  </div>
</template>

<script>
export default {
  // Propiedades reactivas en vue
  data() {
    //opcion mas de openapi
    return {
      numero: this.inicio,
      titulo: "Contador",
    };
  },
  // No importa el orden
  // Metodos
  methods: {
    obtenerCuadrados() {
      console.log("Entro a obtener cuadrado");
      return this.numero * this.numero;
    },
    obtenerCubo() {
      return this.numero * this.numero * this.numero;
    },
    incrementar() {
      console.log(this.tit);
      this.numero++;
    },
    decrementar() {
      this.numero--;
    },
  },
  // Propiedades computadas
  // Solo se ejecutan cuando solo si cambia el resultado del cuerpo, caso contrario no se ejecuta la propiedad lo guarda en cache
  computed: {
    calcularCuadrados() {
      console.log("Entro a propiedad computada");
      return this.numero * this.numero;
    },
    calcularCubo() {
      return this.numero * this.numero * this.numero;
    },
  },

  // Props
  // Son variables que yo puedo instanciar o dar un valor, extermo de mi componente.
  // Variables a nivel de componente, son seteados por el padre
  //props: ["tit", "inicio", "mostrar"], // declaracion basica de props.
  props: {
    tit: String,
    // con mas detalle
    inicio: {
      type: Number,
      default: 99,
      validator(value) {
        return value > 10;
      },
    },
    mostrar: Boolean,
  },
  /* String, Numbre, Boolean, Array, Object, Date, Function, BigInt */
};
</script>

<style>
</style>