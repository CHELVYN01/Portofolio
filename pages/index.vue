<script setup lang="ts">
import AppFooter from '~/components/AppFooter.vue';
import Skill from '~/components/Skill.vue';
import Hero from '~/components/Hero.vue';
import Navbar from '~/components/Navbar.vue';
import Newsletter from '~/components/Newsletter.vue';
import Project from '~/components/Project.vue';
import Karir from '~/components/Carer.vue';
import { onMounted, ref } from "vue";

const isPlaying = ref(false);
let audio: HTMLAudioElement | null = null;

function toggleAudio() {
  if (!audio) return;
  
  if (isPlaying.value) {
    audio.pause();
  } else {
    audio.muted = false;
    audio.play().catch((e: Error) => console.error(e));
  }
  
  isPlaying.value = !isPlaying.value;
}

onMounted(() => {
  audio = new Audio('/music/background.mp3');
  audio.volume = 0.5;
  audio.loop = true;
  
  // Mendeteksi ketika audio selesai atau di-pause
  audio.addEventListener('pause', () => {
    isPlaying.value = false;
  });
  
  audio.addEventListener('play', () => {
    isPlaying.value = true;
  });
  
  // Autoplay dengan muted untuk menghindari kebijakan browser
  audio.muted = true;
  audio.play().catch((e: Error) => console.error(e));
})
</script>

<template>
  <div>
    <Navbar />
    <Hero />
    <Project />
    <Skill />
    <Karir />
    <Newsletter />
    <AppFooter />
    
    <!-- Tombol musik floating dengan Tailwind CSS -->
    <button 
      @click="toggleAudio" 
      class="fixed bottom-8 right-8 z-50 bg-green-500 hover:bg-green-600 text-white rounded-full p-4 shadow-lg transition-all duration-300 hover:scale-110 animate-pulse"
    >
      <svg v-if="isPlaying" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 9v6m4-6v6" />
      </svg>
      <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z" />
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
      </svg>
    </button>
  </div>
</template> 