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
  console.log(guitarra);
  const existeCarrito = carrito.value.findIndex(
    (producto) => producto.id === guitarra.id
  );

  if (existeCarrito >= 0) {
    carrito.value[existeCarrito].cantidad++;
  } else {
    guitarra.cantidad = 1;
    carrito.value.push(guitarra);
  }
};

const decrementarCantidad = (id) => {
  console.log("decrementando");
  const index = carrito.value.findIndex((producto) => producto.id === id);

  if (carrito.value[index].cantidad <= 1) return;
  carrito.value[index].cantidad--;
};

const incrementandoCantidad = (id) => {
  console.log("incrementando");
  const index = carrito.value.findIndex((producto) => producto.id === id);

  if (carrito.value[index].cantidad >= 5) {
  } else {
    carrito.value[index].cantidad++;
  }
};
</script>

<template>
  <Header
    :carrito="carrito"
    @decrementar-cantidad="decrementarCantidad"
    @incrementando-cantidad="incrementandoCantidad"
  />

  <main class="container-xl mt-5">
    <h2 class="text-center">Nuestra Colección</h2>

    <div class="row mt-5">
      <guitarra
        v-for="guitarra in guitarras"
        v-bind:guitarra="guitarra"
        @agregarCarrito="agregarCarrito"
      />
    </div>
  </main>
  <Footer />
</template>

<style scoped></style>
