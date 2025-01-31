<!-- src/views/ContactPhone.vue -->
<script setup>
defineEmits(['close']);
</script>

<template>
    <div class="contact-modal">
        <h2>Contact Me</h2>
        <div class="contact-content">
            <p>Email: your.email@example.com</p>
            <p>LinkedIn: linkedin.com/in/your-profile</p>
            <p>GitHub: github.com/yourusername</p>
        </div>
        <button @click="$emit('close')" class="close-btn">Close</button>
    </div>
</template>

<style scoped>
.contact-modal {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    max-width: 400px;
    width: 90%;
}

.close-btn {
    margin-top: 1rem;
    padding: 0.5rem 1rem;
}
</style>