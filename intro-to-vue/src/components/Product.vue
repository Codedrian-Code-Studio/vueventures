<script setup>
import { ref, defineProps, defineEmits } from 'vue';
import DynamicImage from './DynamicImage.vue';

const props = defineProps({
	cart: {
		type: Object,
		required: true
		}
	});
const emit = defineEmits(['updateCart']);
function addToCart(color) {
	emit('updateCart', color);
}
const inStock = ref(true);
const stock = ref(10);
const productDetails = ref(['30% wool', '50% cotton', '20% polyester']);
const sockImage = ref('socks_green');
const variants = ref([
	{ id: 2233, color: 'green', image: 'socks_green', stock: 199},
	{ id: 2234, color: 'blue', image: 'socks_blue', stock: 10},
]);
const selectedVariant = ref(0);

function incrementStock() {
	return stock.value++;
}
function updateVariant(variant, index) {
	sockImage.value = variant.image;
	inStock.value = variant.stock > 0;
	selectedVariant.value = index;
}
</script>
<template>
	<p>{{ variants[selectedVariant].id }}</p>
	<div class="flex h-2/4">
		<DynamicImage :imageName="sockImage" altText="Product 1 Image" />
		<section class="w-2/4">
			<div class="flex items-center h-16">
				<form v-if="(inStock == true) && (stock > 0)" action="" class="flex w-1/2 ml-3 h-fit">
					<label for="stock" class="h-10 pt-1">In stock:</label>
					<input type="text" class="h-10 w-3/5 text-center ml-3 rounded-md" v-model.number="stock">
				</form>
				<p v-else="inStock = false" class="w-1/2">Out of Stock</p>
				<button v-on:click="incrementStock" :disabled="stock == 0">Add stock</button>
			</div>
			<div class="flex flex-row pt-2">
				<div class="w-3/4">
					<h3>Details</h3>
					<ul class="text-left w-1/4 mx-auto">
						<li v-for="detail in  productDetails">{{ detail }}</li>
					</ul>
					<button class="w-2/5 mx-auto mt-5" @click="addToCart(variants[selectedVariant].color)" :disabled="!inStock" :class="{hidden: !inStock}">Add to cart</button>
				</div>
				<div class="w-1/4">
					<h3>Variants</h3>
					<ul>
						<li v-for="(variant, index) in variants"
							:key="id"
							@click="updateVariant(variant, index)" class="hover:bg-blue-700 text-left">
							<span>{{ variant.color }}</span>
						</li>
					</ul>
				</div>
			</div>
		</section>
	</div>
</template>
