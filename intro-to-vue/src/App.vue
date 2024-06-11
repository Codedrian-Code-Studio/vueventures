<script setup>
import { ref } from 'vue';
import Product from './components/Product.vue'

const cart = ref(10);

</script>
<template>
  <p>Cart: {{ cart }}</p>
  <Product :cart="cart" @update-cart="cart = $event"/>
  <Product :cart="cart" @update-cart="cart = $event"/>
</template>

<!-- <style>
</style> -->
