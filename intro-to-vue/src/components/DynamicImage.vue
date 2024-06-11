<script setup>
import {computed} from 'vue';

const props = defineProps({
    imageName: {
        type: String,
        required: true
    },
    altText: {
        type: String,
        default: ""
    },
    imageClass: {
        type: String,
        default: ""
    }
});

const imageSrc = computed(() => {
    return new URL(`../assets/images/${props.imageName}.jpg`, import.meta.url).href;
});
</script>

<template>
    <img :src="imageSrc" :alt="altText" :class="imageClass">
</template>
