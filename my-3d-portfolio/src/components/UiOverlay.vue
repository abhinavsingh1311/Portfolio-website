<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
    <div class="ui-overlay">
        <!-- Navigation Header -->
        <nav class="header">
            <RouterLink to="/" class="logo">YourName</RouterLink>
            <div class="nav-links">
                <RouterLink to="/work">Work</RouterLink>
                <RouterLink to="/about">About</RouterLink>
                <RouterLink to="/contact">Contact</RouterLink>
            </div>
        </nav>

        <!-- Footer -->
        <div class="footer">
            <div class="social-links">
                <a href="#">LinkedIn</a>
                <a href="#">GitHub</a>
                <a href="#">Twitter</a>
            </div>
        </div>
    </div>
</template>

<style scoped>
.ui-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    mix-blend-mode: difference;
    color: white;
    z-index: 100;
}

.header {
    padding: 2rem;
    display: flex;
    justify-content: space-between;
}

.logo {
    font-size: 1.5rem;
    font-weight: 500;
    text-decoration: none;
    color: inherit;
}

.nav-links a {
    margin-left: 2rem;
    text-decoration: none;
    color: inherit;
}

.footer {
    position: fixed;
    bottom: 2rem;
    left: 2rem;
}

.social-links a {
    display: block;
    margin-bottom: 0.5rem;
    text-decoration: none;
    color: inherit;
}
</style>