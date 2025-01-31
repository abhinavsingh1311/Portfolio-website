<script setup>
import { Renderer, Scene, Camera, OrbitControls } from 'troisjs';
import Computer from '@/components/Computer.vue';
import Bookshelf from '@/components/Bookshelf.vue';
import Phone from '@/components/Phone.vue';
import { ref } from 'vue';
import ResumeModal from './ResumeModal.vue';
import AboutBook from './AboutBook.vue';
import ContactPhone from './ContactPhone.vue';

const showResume = ref(false);
const showAbout = ref(false);
const showContact = ref(false);
</script>

<template>
  <Renderer antialias>
    <Camera :position="{ z: 10 }" />
    <Scene>
      <!-- Interactive 3D Objects -->
      <Computer @click="showResume = true" />
      <Bookshelf @click="showAbout = true" />
      <Phone @click="showContact = true" />

      <!-- Lighting -->
      <PointLight :position="{ y: 10, z: 10 }" :intensity="1" />
      <AmbientLight :intensity="0.5" />

      <!-- Camera Controls -->
      <OrbitControls />
    </Scene>
  </Renderer>

  <!-- Overlay Modals -->
  <ResumeModal v-if="showResume" @close="showResume = false" />
  <AboutBook v-if="showAbout" @close="showAbout = false" />
  <ContactPhone v-if="showContact" @close="showContact = false" />
</template>