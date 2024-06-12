<script setup>
import { ref, defineEmits } from 'vue'
const reviewForm = ref({
    name: '',
    review: '',
})
const emit = defineEmits(['review-submitted'])
function onSubmit() {
    if ((reviewForm.value.name == '') || ((reviewForm.value.review == ''))) {
        return alert('Please enter a name and a value')
    }
    const productReview = {
        name: reviewForm.value.name,
        review: reviewForm.value.review
    }
    reviewForm.value.name = '';
    reviewForm.value.review = '';
    emit('review-submitted', productReview)
}
</script>
<template>
    <form action="" class="flex flex-col w-2/5 mx-auto"  @submit.prevent="onSubmit">
        <label for="name">Name</label>
        <input type="text" name="name" v-model="reviewForm.name">
        <label for="review">Review</label>
        <input type="text" name="review" v-model="reviewForm.review">
        <input type="submit" class="hover:bg-blue-700">
    </form>
</template>
