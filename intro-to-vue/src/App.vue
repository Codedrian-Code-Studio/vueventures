<script setup>
import { ref } from 'vue';
import Product from './components/Product.vue'
import ReviewForm from './components/ReviewForm.vue'
import ReviewList from './components/ReviewList.vue';
const reviews = ref([]);
const cart = ref([]);
function updateCart(color) {
  cart.value.push(color);
}
function displayReview(review) {
  console.log(review)
  reviews.value.push(review);
}
</script>

<template>
  <!-- <p>Cart: {{ cart.length }}</p>
  <Product :cart="cart" @update-cart="updateCart"/> -->
  <ReviewForm  @review-submitted="displayReview"/>
  <ReviewList :reviews="reviews" class="mt-5"/>
</template>

<!--TODO:
2. Create a ReviewList component -->
