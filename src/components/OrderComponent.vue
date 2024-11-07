<script setup>
    import { inject, ref } from 'vue';

    const orderName = ref('');

    const carrito = inject('carrito')
    const reset = inject('resetCarrito')

    function placeOrder() {
        alert(`${carrito.value.map(item => item.name).join(', ')}`);
        orderName.value = '';
        reset();
    }
</script>

<template>
    <div>
        <input v-model="orderName" placeholder="Nom de la comanda..." />
        <button @click="placeOrder">Place Order</button>
    </div>
</template>