<script setup>
import {
  Renderer,
  Scene,
  Camera,
  PointLight,
  AmbientLight,
} from 'troisjs';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls';
import { ref, onMounted, onUnmounted } from 'vue';
import Computer from '../components/Computer.vue';
import Bookshelf from '../components/Bookshelf.vue';
import Phone from '../components/Phone.vue';
import ResumeModal from './ResumeModal.vue';
import AboutBook from './AboutBook.vue';
import ContactPhone from './ContactPhone.vue';

const showResume = ref(false);
const showAbout = ref(false);
const showContact = ref(false);
const renderer = ref(null);
let controls;

onMounted(() => {
  if (renderer.value?.three) {
    // Configure renderer with white background
    renderer.value.three.renderer.setClearColor(0xffffff, 1);
    renderer.value.three.renderer.shadowMap.enabled = true;

    controls = new OrbitControls(
      renderer.value.three.camera,
      renderer.value.three.renderer.domElement
    );

    // Configure controls for better UX
    controls.enableDamping = true;
    controls.dampingFactor = 0.05;
    controls.enableZoom = true;
    // In onMounted()
    controls.minDistance = 8;  // Was 5
    controls.maxDistance = 25; // Was 15
    controls.enablePan = false;
    controls.minPolarAngle = Math.PI / 3;
    controls.maxPolarAngle = Math.PI / 2.5;
    controls.target.set(0, 0.5, 0);

    // Animation loop
    const animate = () => {
      requestAnimationFrame(animate);
      controls.update();
    };
    animate();
  }
});

onUnmounted(() => {
  if (controls) {
    controls.dispose();
  }
});
</script>

<template>
  <div class="scene-container">
    <!-- 3D Scene -->
    <Renderer ref="renderer" antialias resize="window">
      <Camera :position="{ x: 10, y: 9, z: 15 }" />
      <Scene>
        <!-- Adjusted 3D Models with proper scale and position -->
        <Computer @click="showResume = true" :position="{ x: 0, y: 0, z: 0 }" :scale="{ x: 0.8, y: 0.5, z: 0.5 }" />
        <Bookshelf @click="showAbout = true" :position="{ x: -1, y: 5, z: -3 }" :scale="{ x: 5, y: 5, z: 6 }"
          :rotation="{ y: -Math.PI / -1.2 }" />
        <Phone @click="showContact = true" :position="{ x: -7, y: 2, z: -30 }" :scale="{ x: 1.5, y: 1.5, z: 1.5 }"
          :rotation="{ y: 0.13, z: 0 }" />

        <!-- Enhanced Lighting -->
        <AmbientLight :intensity="0.8" />
        <PointLight :position="{ x: 5, y: 8, z: 5 }" :intensity="1.2" cast-shadow />
        <PointLight :position="{ x: -5, y: 8, z: -5 }" :intensity="0.8" cast-shadow />
      </Scene>
    </Renderer>

    <!-- Modal Components -->
    <Transition name="fade">
      <ResumeModal v-if="showResume" @close="showResume = false" />
    </Transition>

    <Transition name="fade">
      <AboutBook v-if="showAbout" @close="showAbout = false" />
    </Transition>

    <Transition name="fade">
      <ContactPhone v-if="showContact" @close="showContact = false" />
    </Transition>

    <!-- Instructions -->
    <div class="instructions" v-if="!showResume && !showAbout && !showContact">
      <p>Click on objects to interact</p>
    </div>
  </div>
</template>

<style scoped>
.scene-container {
  width: 100%;
  height: 100vh;
  position: relative;
  background: white;
}

/* Make renderer fullscreen */
:deep(canvas) {
  position: fixed;
  top: 0;
  left: 0;
}

/* Modal transitions */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Instructions */
.instructions {
  position: fixed;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  color: rgba(0, 0, 0, 0.8);
  padding: 0.5rem 1rem;
  border-radius: 4px;
  font-size: 0.9rem;
  pointer-events: none;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(2px);
  border: 1px solid rgba(0, 0, 0, 0.1);
}

@media (max-width: 768px) {
  .instructions {
    font-size: 0.8rem;
    bottom: 1rem;
  }
}

/* Interactive cursor */
:deep(.interactive) {
  cursor: pointer;
  transition: transform 0.3s ease;
}

:deep(.interactive:hover) {
  transform: scale(1.02);
}
</style>