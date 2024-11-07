<script setup>
  // imports
  import OrderComponent from './components/OrderComponent.vue';
  import ProductListComponent from './components/ProductListComponent.vue';
  import { ref, provide, computed} from 'vue';

  // valor reactiu actual es el dolar
  const currency = ref('dol')

  // array reactiu pels productes 
  const products = ref([
        { name: "Hamburger 🍔.", price: 5 },
      { name: "Cheeseburger 🧀", price: 6 },
      { name: "Impossible Burger 🥕", price: 7 },
      { name: "Fries 🍟", price: 2 }
  ])

  const orderName = ref('')
  const carrito = ref([]);

  const moneda = computed(() => (
    currency.value === 'dol' ? '$' : '€'
  ));

  provide('moneda', moneda);
  provide('products', products);
  provide('cart', carrito);
  provide('orderName', orderName);

  function resetCarrito() {
    carrito.value = []
  };

  provide('resetCarrito', resetCarrito);

</script>


<template>
  <div id="app">
    
    <div id="contenedor">
      <h1>{{orderName || "Nuevo pedido" }}</h1>
      <OrderComponent/>

    <!-- apartado de elegir la moneda -->
    <label for="currency">Currency</label>
    <select v-model="currency" id="currency">
      <option value="dol">Dollar ($)</option>
      <option value="eur">Euro (€)</option>
    </select>
    <ProductListComponent />
    </div>
    
  </div>
</template>
<style scoped>

</style>
