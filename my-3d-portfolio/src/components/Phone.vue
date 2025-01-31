<!-- src/components/Phone.vue -->
<script setup>
import { GltfModel } from 'troisjs';
import { ref } from 'vue';

const modelUrl = new URL('../assets/models/phone.glb', import.meta.url).href;
const emit = defineEmits(['click']);
const modelError = ref(null);
</script>

<template>
    <GltfModel :src="modelUrl" @click="emit('click')" :position="{ x: -3, y: 1, z: 0 }"
        :scale="{ x: 0.5, y: 0.5, z: 0.5 }" :rotation="{ y: Math.PI / 4 }" @error="(err) => modelError = err" />
</template>