<template>

  <div class="contenedor">
    <Tarjeta
      v-for="item in listaDeDatos"
      :nombreRed="item.nombreRed"
      :estado="item.estado"
      :fecha_hora="item.fecha_hora"
    />
  </div>
</template>


<script setup>
import { ref, onMounted } from 'vue' 
import Tarjeta from './components/Tarjeta.vue'

//Inicializamos como un ref vacío (un array por defecto)
const listaDeDatos = ref([]);

async function pideDatos() {
  try {
    const response = await fetch('http://localhost:8080/registros-redes');
    
    if (!response.ok) {
      throw new Error(`Error ${response.status}: ${response.statusText}`);
    }

    const myData = await response.json();
    
    listaDeDatos.value = myData;

  } catch (error) {
    console.error("Hubo un error al obtener los datos:", error);
  }
}

onMounted(() => {
  pideDatos();
  setInterval(pideDatos, 20000)
});


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
