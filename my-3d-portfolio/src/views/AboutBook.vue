<!-- src/views/AboutBook.vue -->
<script setup>
defineEmits(['close']);
</script>

<template>
  <div class="book-overlay">
    <div class="book-modal">
      <div class="book-cover">
        <h2>About Me</h2>
        <button @click="$emit('close')" class="close-btn">✕</button>
      </div>
      <div class="book-content">
        <section>
          <h3>Who I Am</h3>
          <p>Passionate full-stack developer with expertise in creating immersive 3D web experiences...</p>
        </section>
        <section>
          <h3>Technical Expertise</h3>
          <ul>
            <li>React/Next.js</li>
            <li>Three.js/Trois.js</li>
            <li>ASP.NET Core</li>
            <li>Cloud Deployment</li>
          </ul>
        </section>
      </div>
    </div>
  </div>
</template>

<style scoped>
.book-content section {
  margin-bottom: 2rem;
}

.book-content h3 {
  color: #2c3e50;
  margin-bottom: 0.5rem;
}

.book-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
}

.book-modal {
  background: #f5e6d3;
  width: 70%;
  max-width: 800px;
  min-height: 500px;
  border-radius: 8px;
  padding: 2rem;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
  position: relative;
}

.book-content {
  display: grid;
  gap: 1.5rem;
  padding: 1rem;
}

.close-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  border: none;
  font-size: 1.2rem;
  cursor: pointer;
}
</style>