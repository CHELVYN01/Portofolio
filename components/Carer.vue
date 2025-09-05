<template>
  <section id="career" class="py-16 px-6 bg-gradient-to-t from-black via-[#000301] to-[#000A03] text-white">
    <h2 class="text-4xl font-bold text-center text-green-400">Career Journey</h2>
    <p class="text-center text-gray-400 mt-2">My professional milestones & experiences</p>

    <div class="relative mt-10 max-w-5xl mx-auto overflow-hidden">
      <!-- Career Timeline -->
      <div class="flex transition-transform duration-500 ease-in-out"
        :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
        <div v-for="(career, index) in careerTimeline" :key="index"
          class="min-w-full flex flex-col items-center text-center px-8">
          <div class="p-8 bg-[#0A1B2F] rounded-2xl shadow-lg border border-green-500 w-3/4">
            <span class="text-green-300 text-sm font-medium">{{ career.year }}</span>
            <h3 class="text-2xl font-semibold mt-2 text-green-400">{{ career.title }}</h3>
            <p class="mt-2 text-gray-300">{{ career.description }}</p>
            <div class="mt-4 flex justify-center gap-4">
              <a :href="career.link" target="_blank" class="text-green-300 hover:text-green-500">
                🔗 Go to Link
              </a>

            </div>
          </div>
        </div>
      </div>

      <!-- Navigation Buttons -->
      <button @click="prevSlide"
        class="absolute left-0 top-1/2 transform -translate-y-1/2 bg-black bg-opacity-50 p-3 rounded-full text-green-400 hover:bg-opacity-70">
        ❮
      </button>
      <button @click="nextSlide"
        class="absolute right-0 top-1/2 transform -translate-y-1/2 bg-black bg-opacity-50 p-3 rounded-full text-green-400 hover:bg-opacity-70">
        ❯
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

// const startAutoSlide = () => {
//   interval = setInterval(() => {
//     nextSlide();
//   }, 5000);
// };

// const stopAutoSlide = () => {
//   clearInterval(interval);
// };

onMounted(() => {
  nextSlide()
});

onUnmounted(() => {
  stopAutoSlide();
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