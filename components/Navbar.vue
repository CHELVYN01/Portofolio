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
          link.classList.add("text-[#C9A961]");
        } else {
          link.classList.remove("text-[#C9A961]");
        }
      }
    });
  });
});
</script>

<template>
  <!-- Navbar -->
  <nav class="bg-[#FAF8F3] fixed w-full top-0 z-10 py-5 px-8 flex justify-between items-center text-[#1B2845] shadow-lg border-b-2 border-[#D4C5B0]">
    <!-- Logo -->
    <NuxtLink to="#hero" @click.prevent="smoothScroll('#hero')" class="text-3xl font-bold text-[#1B2845] tracking-wide">
      Chelvyn Kleden
    </NuxtLink>

    <!-- Desktop Menu -->
    <ul class="hidden md:flex space-x-8 text-lg">
      <li><a href="#projects" @click.prevent="smoothScroll('#projects')" class="nav-link hover:text-[#C9A961] transition-all duration-300 font-medium">Projects</a></li>
      <li><a href="#skills" @click.prevent="smoothScroll('#skills')" class="nav-link hover:text-[#C9A961] transition-all duration-300 font-medium">Skills</a></li>
      <li><a href="#career" @click.prevent="smoothScroll('#career')" class="nav-link hover:text-[#C9A961] transition-all duration-300 font-medium">Career</a></li>
    </ul>

    <!-- Kontak -->
    <div class="hidden md:flex space-x-4 items-center">
      <a href="https://wa.me/6285803480139" target="_blank" rel="noopener"
        class="bg-[#1B2845] text-[#FAF8F3] px-6 py-2 border-2 border-[#1B2845] hover:bg-[#C9A961] hover:border-[#C9A961] hover:text-[#1B2845] transition-all duration-300 font-semibold">
        Contact
      </a>
    </div>

    <!-- Mobile Menu Button -->
    <button class="md:hidden focus:outline-none" @click="isOpen = !isOpen">
      <svg class="w-6 h-6 text-[#1B2845]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
      </svg>
    </button>

    <!-- Mobile Menu -->
    <div v-if="isOpen" class="absolute top-[72px] left-0 w-full bg-[#FAF8F3] md:hidden border-b-2 border-[#D4C5B0] shadow-lg">
      <ul class="flex flex-col space-y-4 p-6 text-[#1B2845]">
        <li><a href="#projects" @click.prevent="smoothScroll('#projects')" class="nav-link hover:text-[#C9A961] transition-colors duration-300 font-medium">Projects</a></li>
        <li><a href="#skills" @click.prevent="smoothScroll('#skills')" class="nav-link hover:text-[#C9A961] transition-colors duration-300 font-medium">Skills</a></li>
        <li><a href="#career" @click.prevent="smoothScroll('#career')" class="nav-link hover:text-[#C9A961] transition-colors duration-300 font-medium">Career</a></li>
        <li class="border-t-2 border-[#D4C5B0] pt-4">
          <NuxtLink to="#contact" class="bg-[#1B2845] text-[#FAF8F3] px-6 py-2 border-2 border-[#1B2845] hover:bg-[#C9A961] hover:border-[#C9A961] hover:text-[#1B2845] transition-all duration-300 font-semibold block text-center">
            Contact
          </NuxtLink>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style scoped></style>
