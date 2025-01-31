<script setup>
defineProps({
    castShadow: Boolean,
    receiveShadow: Boolean,
});
</script>

<template>
    <primitive :object="model" :cast-shadow="castShadow" :receive-shadow="receiveShadow" />
</template>