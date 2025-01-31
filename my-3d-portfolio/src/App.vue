<!-- src/App.vue -->
<template>
  <div class="app-container">
    <RouterView />
  </div>
</template>

<style>
html,
body,
#app {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background: rgb(82, 90, 133);
  /* Pure white background */
}

/* Make canvas slightly transparent to blend with white */
canvas {
  opacity: 0.98;
  mix-blend-mode: multiply;
}
</style>