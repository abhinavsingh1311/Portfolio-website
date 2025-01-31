<script setup>
import GltfWrapper from './GltfWrapper.vue';

defineProps({
  castShadow: Boolean,
  receiveShadow: Boolean
});

const modelUrl = new URL('../assets/models/computer.glb', import.meta.url).href;
</script>

<template>
  <GltfWrapper :src="modelUrl" :cast-shadow="castShadow" :receive-shadow="receiveShadow" @click="$emit('click')" />
</template>