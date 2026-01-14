<template>
    <div class="card" :class="{ 'borderojo': props.estado === 'SIN_SENAL', 'bordeverde': props.estado === 'CONECTADO', 'bordeamarillo': props.estado === 'FALLO_AUTH' }">
        <h3>{{ nombre }}</h3>
        <p class="estado" :class="{ 'textrojo': props.estado === 'SIN_SENAL', 'textverde': props.estado === 'CONECTADO', 'textamarillo': props.estado === 'FALLO_AUTH' }">{{ estado }}</p>
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
    color: white;
}

.fecha {
    font-size: 1.5em;
    color: #ddd;
}

p {
    margin: 5px 0;
}

.borderojo{
    border-color: #c20202;
    background-color: #c202026e;
}

.bordeverde{
    border-color: rgb(36, 156, 36);
    background-color:  rgba(59, 161, 0, 0.466);
}

.bordeamarillo{
    border-color: #f0ad00;
    background-color: #f0ac0073;
}

.textverde{
color:rgb(36, 156, 36);
}

.textrojo{
color: #c20202;
}

.textamarillo{
color: #f0ad00;
}
</style>