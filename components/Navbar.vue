<script setup>
import { ref, onMounted } from "vue";

const isOpen = ref(false);

// Fungsi untuk scroll halus ke section yang dituju
const smoothScroll = (id) => {
  const section = document.querySelector(id);
  if (section) {
    window.scrollTo({
      top: section.offsetTop - 80,
      behavior: "smooth",
    });
  }
  isOpen.value = false; // Tutup menu saat di mobile
};



// Tambahkan event listener untuk highlight menu aktif
onMounted(() => {
  window.addEventListener("scroll", () => {
    document.querySelectorAll("nav a").forEach((link) => {
      const section = document.querySelector(link.getAttribute("href"));
      if (section) {
        const top = window.scrollY;
        const offset = section.offsetTop - 100;
        const height = section.offsetHeight;

        if (top >= offset && top < offset + height) {
          link.classList.add("text-green-400");
        } else {
          link.classList.remove("text-green-400");
        }
      }
    });
  });
});
</script>

<template>
  <!-- Navbar -->
  <nav class="bg-[#000A03] fixed w-full top-0 z-10 py-4 px-6 flex justify-between items-center text-white shadow-md">
    <!-- Logo -->
    <NuxtLink to="#hero" @click.prevent="smoothScroll('#hero')" class="text-2xl font-bold text-green-400">ChelvynKleden
    </NuxtLink>

    <!-- Desktop Menu -->
    <ul class="hidden md:flex space-x-6">
      <li><a href="#projects" @click.prevent="smoothScroll('#projects')" class="nav-link">Projects</a></li>
      <li><a href="#skills" @click.prevent="smoothScroll('#skills')" class="nav-link">Skills</a></li>
      <li><a href="#career" @click.prevent="smoothScroll('#career')" class="nav-link">Career</a></li>
    </ul>

    <!-- Kontak -->
    <div class="hidden md:flex space-x-4 items-center">
      <a href="https://wa.me/6285803480139" target="_blank" rel="noopener"
        class="bg-green-600 text-black px-4 py-2 rounded-lg hover:bg-green-500">
        Contact
      </a>
    </div>

    <!-- Mobile Menu Button -->
    <button class="md:hidden focus:outline-none" @click="isOpen = !isOpen">
      <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
      </svg>
    </button>

    <!-- Mobile Menu -->
    <div v-if="isOpen" class="absolute top-16 left-0 w-full bg-[#18230F] md:hidden">
      <ul class="flex flex-col space-y-4 p-4 text-white">
        <li><a href="#projects" @click.prevent="smoothScroll('#projects')" class="nav-link">Projects</a></li>
        <li><a href="#skills" @click.prevent="smoothScroll('#skills')" class="nav-link">Skills</a></li>
        <li><a href="#career" @click.prevent="smoothScroll('#career')" class="nav-link">Career</a></li>
        <li class="border-t border-gray-700 pt-4">
          <NuxtLink to="#contact" class="bg-green-600 text-black px-4 py-2 rounded-lg block text-center">Contact
          </NuxtLink>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style scoped></style>
