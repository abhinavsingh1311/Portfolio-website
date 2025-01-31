<script setup>
import { GltfModel } from 'troisjs';

defineProps({
    src: String,
    castShadow: Boolean,
    receiveShadow: Boolean
});

defineEmits(['click']);
</script>

<template>
    <GltfModel :src="src" @click="$emit('click')" :cast-shadow="castShadow" :receive-shadow="receiveShadow" />
</template>