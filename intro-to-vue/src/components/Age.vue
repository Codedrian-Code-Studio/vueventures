<script setup>

import { ref, computed } from 'vue'
const inStock = ref(true);
const stock = ref(10);
const productDetails = ref(['30% wool', '50% cotton', '20% polyester']);

function incrementStock() {
	return stock.value++;
}
</script>
<template>

	<div class="flex h-2/4">
		<img src="../assets/images/socks_blue.jpg" alt="Blue socks" class="w-2/4"/>
		<section class="w-2/4">
			<div class="flex items-center h-16">
				<form v-if="(inStock == true) && (stock > 0)" action="" class="flex w-1/2 ml-3 h-fit">
					<label for="stock" class="h-10 pt-1">In stock:</label>
					<input type="text" class="h-10 w-3/5 text-center ml-3" v-model.number="stock">
				</form>
				<p v-else="inStock = false" class="w-1/2">Out of Stock</p>
				<button v-on:click="incrementStock">Add stock</button>
			</div>
			<div class="flex flex-col pt-2">
				<h3>Details</h3>
				<ul class="text-left w-1/4 mx-auto">
					<li v-for="detail in  productDetails">{{ detail }}</li>
				</ul>
			</div>
		</section>
	</div>
</template>
