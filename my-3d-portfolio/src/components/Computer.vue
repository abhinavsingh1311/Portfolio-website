<!-- src/components/Computer.vue -->
<script setup>
import { GltfModel } from 'troisjs';
import { ref } from 'vue';

const modelUrl = new URL('../assets/models/low_poly_computer_desk.glb', import.meta.url).href;
const emit = defineEmits(['click']);
const modelError = ref(null);
</script>

<template>
  <GltfModel :src="modelUrl" @click="emit('click')" :position="{ x: 0, y: 1, z: 0 }" :scale="{ x: 0.8, y: 0.8, z: 0.8 }"
    @error="(err) => modelError = err" />
</template>