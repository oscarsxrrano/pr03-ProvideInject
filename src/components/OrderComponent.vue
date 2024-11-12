<script setup>
import { inject } from 'vue';

const orderName = inject('orderName');
const carrito = inject('carrito');
const resetCarrito = inject('resetCarrito');

// funcion 
function placeOrder() {
  alert(`Pedido realizado con éxito! Disfrútalo!
    ${carrito.value.map((producto) => producto.name).join(`, 
    `)}`);
  orderName.value = ''; 
  resetCarrito();
}
</script>

<template>
  <div>
    <input v-model="orderName" placeholder="Nom de la comanda..." />
    <button @click="placeOrder">Place Order</button>
  </div>
</template>
