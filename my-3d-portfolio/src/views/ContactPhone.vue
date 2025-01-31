<script setup>
</script>

<template>
    <div class="contact-modal">
        <h2>Contact Me</h2>
        <p>Email:</p>
        <p>LinkedIn:</p>
        <button @onclick="$emit('close')">Close</button>
    </div>
</template>

<style scoped>
.contact-modal{
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-505,-50%);
    background: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
}
</style>