<!-- In App.vue -->
<template>
  <div class="app-container">
    <nav class="main-nav">
      <RouterLink to="/" class="logo">Abhinav Singh</RouterLink>
    </nav>
    <RouterView />
  </div>
</template>

<style>
.main-nav {
  position: fixed;
  top: 0;
  width: 100%;
  padding: 1.5rem;
  display: flex;
  justify-content: space-between;
  z-index: 100;
  mix-blend-mode: difference;
  color: rgb(206, 203, 214);
}

.logo {
  font-weight: 500;
  text-decoration: none;
  color: inherit;
}

.nav-links a {
  margin-left: 2rem;
  text-decoration: none;
  color: inherit;
}
</style>