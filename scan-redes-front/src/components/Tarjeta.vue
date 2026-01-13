<template>
    <div class="card" :style="{ borderColor: colorDinamico, backgroundColor: colorfondoDinamico }">
        <h3>{{ nombre }}</h3>
        <p class="estado" :style="{ color: colorDinamico }">{{ estado }}</p>
        <p class="fecha">{{ fecha }}</p>
    </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    nombre: String,
    estado: String,
    fecha: String
});

// Lógica del color
const colorDinamico = computed(() => {
    let colorFinal = "#aeaeae";

    switch (props.estado) {
        case "CONECTADO":
            colorFinal = "#53b921"; 
            break;
        case "SIN_SENAL":
            colorFinal = "#c13205";
            break;
        case "FALLO_AUTH":
            colorFinal = "#f0ad00";
            break;
    }
    return colorFinal;
});

const colorfondoDinamico = computed(() => {
    let colorfondoFinal = "#aeaeae";

    switch (props.estado) {
        case "CONECTADO":
            colorfondoFinal = "#54b9217c"; 
            break;
        case "SIN_SENAL":
            colorfondoFinal = "#c1310585";
            break;
        case "FALLO_AUTH":
            colorfondoFinal = "#f0ac0096";
            break;
    }
    return colorfondoFinal;
});

</script>

<style scoped>
.card {
    border: 1px solid #ccc;
    padding: 20px;
    border-radius: 8px;
    color: #333;
    border: 5px solid;
}

h3 {
    color: rgb(255, 255, 255);
    margin: 0 0 10px 0;
    font-size: 3em;
    font-weight: bold;
    text-shadow: 2px 2px 4px #000000;
}

.estado{
    background-color: #252525;
    border-radius: 20px;
    padding: 10px;
    font-weight: bolder;
    width: fit-content;
    box-shadow: 1px 1px 5px #000000;
}

.fecha {
    font-size: 1.5em;
    color: #ddd;
}

p {
    margin: 5px 0;
}
</style>