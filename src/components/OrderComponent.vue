<script setup>
    import { ref } from 'vue';

    const orderName = ref('');

    function placeOrder() {
        alert(`La teva comanda "${orderName.value}" ha sigut enviada!`);
        orderName.value = ''
    }
</script>

<template>
    <div>
        <input v-model="orderName" placeholder="Nom de la comanda..." />
        <button @click="placeOrder">Place Order</button>
    </div>
</template>