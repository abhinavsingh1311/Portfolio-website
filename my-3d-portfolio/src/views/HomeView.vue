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
    // Make renderer transparent
    renderer.value.three.renderer.setClearColor(0x000000, 0);

    controls = new OrbitControls(
      renderer.value.three.camera,
      renderer.value.three.renderer.domElement
    );

    // Configure controls
    controls.enableDamping = true;
    controls.dampingFactor = 0.05;
    controls.enableZoom = true;
    controls.minDistance = 8;
    controls.maxDistance = 20;
    controls.enablePan = false;
    controls.minPolarAngle = Math.PI / 4;
    controls.maxPolarAngle = Math.PI / 2;
    controls.target.set(0, 0, 0);

    // Animation loop
    const animate = () => {
      requestAnimationFrame(animate);
      if (controls) {
        controls.update();
      }
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
    <!-- Background container -->
    <div class="background-container">
      <div class="background-overlay"></div>
    </div>

    <!-- 3D Scene -->
    <Renderer ref="renderer" antialias resize="window" alpha>
      <Camera :position="{ x: 0, y: 2, z: 12 }" />
      <Scene>
        <!-- 3D Models -->
        <Computer @click="showResume = true" :position="{ x: 0, y: -1, z: 0 }" :scale="{ x: 0.8, y: 0.8, z: 0.8 }" />
        <Bookshelf @click="showAbout = true" :position="{ x: 4, y: -1, z: 2 }" :scale="{ x: 0.7, y: 0.7, z: 0.7 }"
          :rotation="{ y: -Math.PI / 6 }" />
        <Phone @click="showContact = true" :position="{ x: -4, y: -0.5, z: 2 }" :scale="{ x: 0.4, y: 0.4, z: 0.4 }"
          :rotation="{ y: Math.PI / 6 }" />

        <!-- Lighting -->
        <AmbientLight :intensity="0.7" />
        <PointLight :position="{ x: 10, y: 10, z: 10 }" :intensity="1" />
        <PointLight :position="{ x: -10, y: 10, z: -10 }" :intensity="0.8" />
        <PointLight :position="{ y: 5, z: 5 }" :intensity="1.2" />
      </Scene>
    </Renderer>

    <!-- Modal Components with Transitions -->
    <Transition name="fade">
      <ResumeModal v-if="showResume" @close="showResume = false" class="modal" />
    </Transition>

    <Transition name="fade">
      <AboutBook v-if="showAbout" @close="showAbout = false" class="modal" />
    </Transition>

    <Transition name="fade">
      <ContactPhone v-if="showContact" @close="showContact = false" class="modal" />
    </Transition>

    <!-- Optional: Add instructions or hover text -->
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
  overflow: hidden;
}

.background-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -2;
}

.background-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.3);
  z-index: -1;
}

/* Make renderer transparent */
:deep(canvas) {
  position: relative;
  z-index: 1;
}

/* Modal styles */
.modal {
  position: fixed;
  z-index: 100;
}

/* Transition animations */
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
  background: rgba(0, 0, 0, 0.7);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  font-size: 0.9rem;
  pointer-events: none;
  opacity: 0.8;
  transition: opacity 0.3s ease;
}

.instructions:hover {
  opacity: 1;
}

/* Optional: Add responsive design */
@media (max-width: 768px) {
  .instructions {
    font-size: 0.8rem;
    bottom: 1rem;
  }
}

/* Optional: Add hover effects for interactive elements */
:deep(.interactive-object:hover) {
  cursor: pointer;
}
</style>