<script setup>
    import { inject } from 'vue';

    // inject para recibir los datos de app.vue
    const products = inject('products')
    const moneda = inject('moneda')
    const carrito = inject('carrito');
    
    // alert del carrito
    function addToCart(product) {
        carrito.value.push(product); 
        alert(carrito.value.map(item => item.name).join(', '));
    }


</script>

<template>
    <div>
        <!-- for per crear un div per a cada producte-->
        <div v-for="product in products" :key="product.name">
            <span>{{ product.name }} - {{ moneda }} {{ product.price }}</span>
            <button @click="addToCart(product)" >Add to Cart</button>
        </div>
    </div>
</template>