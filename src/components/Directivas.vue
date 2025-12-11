<template>
  <div>
    <label for="id_nombre">Nombre:</label>
    <!-- v-model necesita una propiedad reactiva  -->
    <input id="id_nombre" type="text" />
    <p>{{ nombre }}</p>

    <label for="id_apellido">Apellido:</label>
    <input id="id_apellido" type="text" />

    <button v-on:click="imprimirNombre()">Imprimir Nombre</button>
    <button v-on:click="agregarEstudiante()">Agregar Estudiante</button>
    <h1>{{ arreglo }}</h1>
    <br />
    <label for="id_nombre_1">Nombre:</label>
    <input v-on:keypress.enter=" agregarEstudiante1" v-model="nombre" id="id_nombre_1" type="text">
    <label for="id_apellido_1">Apellido:</label>
    <input v-on:keypress.enter=" agregarEstudiante1" v-model="apellido" id="id_apellido_1" type="text">
    <!-- Directiva v-for -->
    <ul>
      <li v-show="nombre" v-for="{ nombre, apellido } in arreglo" :key="nombre">
        {{ nombre }} - {{ apellido }}
      </li>
    </ul>
    <h2>Tabla</h2>
    <table>
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Apellido</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-show="nombre"
          v-for="{ nombre, apellido } in arreglo"
          :key="apellido"
        >
          <td>{{ nombre }}</td>
          <td>{{ apellido }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: null,
      apellido: null,
      arreglo: [],
      //arreglo: [1,2,3,4],
    };
  },

  methods: {
    imprimirNombre() {
      console.log(this.nombre);
    },
    agregarEstudiante() {
      const estu = {
        nombre: this.nombre,
        apellido: this.apellido,
      };
      console.log("Se agrega Estudiante");
      console.log(estu);
      this.arreglo.push(estu);
      this.limpiarFormulario();
    },
     agregarEstudiante1(event) {
      console.log('evento');
      const estu2 = {
        nombre: this.nombre,
        apellido: this.apellido,
      };
      if(event.charCode != 13){
        return;
      }
      this.arreglo.push(estu2);
      this.limpiarFormulario();
      console.log("Presiono el enter");
      console.log("Agrego estudiante 1");
      console.log(event);
      console.log(event.charCode);
     },
    limpiarFormulario() {
      this.nombre = null;
      this.apellido = null;
    },
  },
};
</script>

<style>

table,
tr,
th,
td {
  border: 1px solid black;
  border-collapse: collapse;
  padding: 5px;
}
</style>