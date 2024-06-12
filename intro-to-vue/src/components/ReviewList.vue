<script setup>
import { defineProps } from 'vue';
const props = defineProps({
    reviews: {
        type: Array,
        required: true,
    }
})
</script>
<template>
    <div v-if="props.reviews.length" v-for="review in reviews" class="outline mt-3 bg-blue-800">
        <p>Reviewed by:{{ review.name }}</p>
        <p class="mt-3">{{ review.review }}</p>
    </div>
    <div v-else>No Reviews</div>
</template>
