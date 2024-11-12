<script setup>
// imports
import { inject } from 'vue';

// injects
const products = inject('products');
const moneda = inject('moneda');
const carrito = inject('carrito');

// funcion alert
function addToCart(product) {
  carrito.value.push(product);
  alert(carrito.value.map((item) => item.name).join(', '));
}
</script>

<template>
  <div>
    <!-- v-for para crear un div por cada producto -->
    <div v-for="product in products" :key="product.name">
      <span>{{ product.name }} - {{ moneda }} {{ product.price }}</span>
      <button @click="addToCart(product)">Add to Cart</button>
    </div>
  </div>
</template>