<template>
    <div>
        <h1 style="text-align: center;">Tienda 32 Bits</h1>
      <h3>Lista de Juegos</h3>
      <table class="styled-table">
        <thead>
          <tr>
            <th>Código</th>
            <th>Nombre</th>
            <th>Stock</th>
            <th>Precio</th>
            <th>Color</th>
            <th>Acciones</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="juego in juegos" :key="juego.codigo">
            <td>{{ juego.codigo }}</td>
            <td>{{ juego.nombre }}</td>
            <td>{{ juego.stock }}</td>
            <td>{{ formatearPrecio(juego.precio) }}</td> <!-- Usamos el método para formatear el precio -->
            <td>{{ juego.color }}</td>
            <td>
              <button @click="accionAumentarStock(juego.codigo)">Aumentar Stock</button>
              <button @click="accionDisminuirStock(juego.codigo)">Disminuir Stock</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  import { mapState, mapActions } from "vuex";
  
  export default {
    computed: {
      ...mapState(["juegos"]),
    },
    methods: {
      ...mapActions(["accionAumentarStock", "accionDisminuirStock"]),
      
      // Método para formatear el precio a formato de pesos
      formatearPrecio(precio) {
        return new Intl.NumberFormat('es-CL', {
          style: 'currency',
          currency: 'CLP',
        }).format(precio);
      }
    }
  };
  </script>
  
  <style>
  .styled-table {
    border: 2px solid black;
    border-collapse: collapse;
    width: 100%;
  }
  
  .styled-table th, .styled-table td {
    border: 2px solid black;
    padding: 8px;
    text-align: center;
  }
  </style>
  