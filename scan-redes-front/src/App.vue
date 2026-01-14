<template>

  <div class="contenedor">
    <Tarjeta
      v-for="item in listaDeDatos"
      :nombre="item.nombre"
      :estado="item.estado"
      :fecha="item.fecha"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue' //Variable reactiva
import Tarjeta from './components/Tarjeta.vue'

const listaDeDatos = [
  { nombre: 'Andared', estado: 'CONECTADO', fecha:"12-03-2054" },
  { nombre: 'Andared_Corporativo', estado: 'FALLO_AUTH',fecha:"04-04-2024"},
  { nombre: 'Andared_2', estado: 'SIN_SENAL',fecha:"22-11-2023" },
]
</script>

<style>
  *{
    margin: 0;
    padding: 0;
  }

  .contenedor {
    display: grid;
    grid-template-columns: 2fr 2fr;
    gap: 2em;
    padding: 4em;
  }

</style>
