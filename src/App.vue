<script setup>
import { ref, reactive, onMounted } from "vue";
import { db } from "./data/guitarras";
import guitarra from "./components/Guitarra.vue";
import Header from "./components/Header.vue";

import Footer from "./components/Footer.vue";
// Esto es con reactive para poder manejar objetos o datoas agrupados

// console.log(state.guitarras);

const guitarras = ref([]);
const carrito = ref([]);
onMounted(() => {
  guitarras.value = db;
  // console.log("Componente listo");
});
const agregarCarrito = (guitarra) => {
  // console.log(guitarra);
  guitarra.cantidad = 1;
  carrito.value.push(guitarra);
};
</script>

<template>
  <Header :carrito="carrito" />

  <main class="container-xl mt-5">
    <h2 class="text-center">Nuestra Colección</h2>

    <div class="row mt-5">
      <guitarra
        v-for="guitarra in guitarras"
        v-bind:guitarra="guitarra"
        @agregar-carrito="agregarCarrito"
      />
    </div>
  </main>
  <Footer />
</template>

<style scoped></style>
