<script setup>
import { GLTFModel } from 'troisjs';

const modelUrl = '@/assets/models/low_poly_computer_desk.glb';

// Emit click event to parent
const emit = defineEmits(['click']);
</script>

<template>
  <GLTFModel 
    :src="modelUrl"
    @click="emit('click')"
    :position="{ x: 0, y: 1, z: 0 }"
    :scale="0.5"
  />
</template>