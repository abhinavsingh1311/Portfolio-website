<!-- src/components/Bookshelf.vue -->
<script setup>
import { GltfModel } from 'troisjs';
import { ref } from 'vue';

const modelUrl = new URL('../assets/models/bookshelf_short_lowpoly.glb', import.meta.url).href;
const emit = defineEmits(['click']);
const modelError = ref(null);
</script>

<template>
    <GltfModel :src="modelUrl" @click="emit('click')" :position="{ x: 3, y: 0, z: -2 }"
        :scale="{ x: 0.8, y: 0.8, z: 0.8 }" :rotation="{ y: -Math.PI / 4 }" @error="(err) => modelError = err" />
</template>