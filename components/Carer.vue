<template>
  <section id="career" class="py-20 px-6 bg-[#FAF8F3] text-[#1B2845] border-t-2 border-[#D4C5B0]">
    <!-- Section Header -->
    <div class="text-center mb-12">
      <h2 class="text-5xl font-bold text-[#1B2845] mb-4">Career Journey</h2>
      <div class="w-24 h-1 bg-[#C9A961] mx-auto mb-4"></div>
      <p class="text-[#4A4A4A] text-lg">My professional milestones & experiences</p>
    </div>

    <div class="relative mt-12 max-w-5xl mx-auto overflow-hidden">
      <!-- Career Timeline -->
      <div class="flex transition-transform duration-500 ease-in-out"
        :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
        <div v-for="(career, index) in careerTimeline" :key="index"
          class="min-w-full flex flex-col items-center text-center px-8">
          <div class="p-10 bg-[#F5F1E8] shadow-lg border-4 border-[#C9A961] w-4/5 relative">
            <!-- Decorative Corner Elements -->
            <div class="absolute top-0 left-0 w-8 h-8 border-t-2 border-l-2 border-[#1B2845]"></div>
            <div class="absolute top-0 right-0 w-8 h-8 border-t-2 border-r-2 border-[#1B2845]"></div>
            <div class="absolute bottom-0 left-0 w-8 h-8 border-b-2 border-l-2 border-[#1B2845]"></div>
            <div class="absolute bottom-0 right-0 w-8 h-8 border-b-2 border-r-2 border-[#1B2845]"></div>

            <!-- Content -->
            <span class="text-[#C9A961] text-base font-bold uppercase tracking-wider">{{ career.year }}</span>
            <h3 class="text-3xl font-bold mt-4 text-[#1B2845] leading-tight">{{ career.title }}</h3>
            <p class="mt-4 text-[#4A4A4A] text-lg leading-relaxed">{{ career.description }}</p>
            <div class="mt-6 flex justify-center gap-4">
              <a :href="career.link" target="_blank"
                 class="inline-block bg-[#1B2845] text-[#FAF8F3] px-6 py-2 border-2 border-[#1B2845] hover:bg-[#C9A961] hover:border-[#C9A961] hover:text-[#1B2845] transition-all duration-300 font-semibold">
                Visit Website
              </a>
            </div>
          </div>
        </div>
      </div>

      <!-- Navigation Buttons -->
      <button @click="prevSlide"
        class="absolute left-0 top-1/2 transform -translate-y-1/2 bg-[#1B2845] bg-opacity-80 p-4 text-[#FAF8F3] hover:bg-[#C9A961] hover:text-[#1B2845] transition-all duration-300 text-2xl font-bold">
        ‹
      </button>
      <button @click="nextSlide"
        class="absolute right-0 top-1/2 transform -translate-y-1/2 bg-[#1B2845] bg-opacity-80 p-4 text-[#FAF8F3] hover:bg-[#C9A961] hover:text-[#1B2845] transition-all duration-300 text-2xl font-bold">
        ›
      </button>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const currentIndex = ref(0);
let interval = null;

const careerTimeline = [
  {
    year: "2025 - Present",
    title: "Junior Technical Consultant (Odoo Developer) - PT. Sinergi Karya Solusindo",
    description: "Worked on customizing and developing Odoo modules, automating workflows, and integrating Odoo with business processes. Contributed to building efficient ERP solutions using Python and PostgreSQL.",
    link: "https://www.sinerka.com", // bisa diganti dengan link resmi perusahaan
  },
  {
    year: "2023",
    title: "Web Development Intern - Harian Jogja Group",
    description: "Developed web streaming interfaces using React.js & Tailwind CSS. Enhanced website interactivity and assisted in hardware troubleshooting.",
    link: "https://www.harianjogja.com",

  },
  {
    year: "2023",
    title: "Informatics Project Practicum Assistant - Sanata Dharma University",
    description: "Maintained a professional work environment, greeted guests, and handled incoming calls to process requests and transfer messages.",
    link: "https://www.usd.ac.id",

  },

];

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % careerTimeline.length;
};

const prevSlide = () => {
  currentIndex.value = (currentIndex.value - 1 + careerTimeline.length) % careerTimeline.length;
};

onMounted(() => {
  nextSlide()
});
</script>

<style>
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

section {
  animation: fadeIn 0.8s ease-out;
}
</style>