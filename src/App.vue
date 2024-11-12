<script setup>
// imports
import OrderComponent from './components/OrderComponent.vue';
import ProductListComponent from './components/ProductListComponent.vue';
import { ref, provide, computed } from 'vue';


// moneda reactiva 
const currency = ref('dol');

// array productos
const products = ref([
  { name: 'Hamburger 🍔', price: 5 },
  { name: 'Cheeseburger 🧀', price: 6 },
  { name: 'Impossible Burger 🥕', price: 7 },
  { name: 'Fries 🍟', price: 2 },
]);


const orderName = ref('');
const carrito = ref([]);

// cambio moneda
const convertedProducts = computed(() => {
  const conversionRate = currency.value === 'eur' ? 0.94 : 1;
  return products.value.map(product => ({
    ...product,
    price: (product.price * conversionRate).toFixed(2),
  }));
});

const moneda = computed(() => (currency.value === 'dol' ? '$' : '€'));


// provides
provide('moneda', moneda);
provide('products', convertedProducts);
provide('carrito', carrito );
provide('orderName', orderName);

// funcion para borrar array del carrito
function resetCarrito() {
  carrito.value = [];
}

provide('resetCarrito', resetCarrito);
</script>

<template>
  <div id="app">
    <div id="contenedor">
      <h1>{{ orderName || 'Nuevo pedido' }}</h1>
      
      <OrderComponent />

      <!-- elegir moneda -->
      <label for="currency">Currency</label>
      <select v-model="currency" id="currency">
        <option value="dol">Dollar ($)</option>
        <option value="eur">Euro (€)</option>
      </select>

      <ProductListComponent/>
    </div>
  </div>
</template>

<style scoped></style>
