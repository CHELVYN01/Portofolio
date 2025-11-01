<template>
  <!-- Projects Section -->
  <section id="projects" class="py-20 px-6 bg-[#FAF8F3] text-[#1B2845] border-t-2 border-[#D4C5B0]">
    <!-- Section Header -->
    <div class="text-center mb-12">
      <h2 class="text-5xl font-bold text-[#1B2845] mb-4">My Projects</h2>
      <div class="w-24 h-1 bg-[#C9A961] mx-auto mb-4"></div>
      <p class="text-[#4A4A4A] text-lg">Check out some of my recent work</p>
    </div>

    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-8 mt-12 max-w-6xl mx-auto">
      <div v-for="(project, index) in projects" :key="index"
        class="p-8 bg-[#F5F1E8] border-2 border-[#D4C5B0] shadow-md text-center transition-all duration-300 hover:shadow-xl hover:-translate-y-2 hover:border-[#C9A961]">

        <!-- Decorative Top Border -->
        <div class="w-16 h-1 bg-[#C9A961] mx-auto mb-6"></div>

        <h3 class="text-2xl font-bold text-[#1B2845] mb-3">{{ project.name }}</h3>
        <p class="mt-3 text-[#4A4A4A] text-base leading-relaxed">{{ project.description }}</p>

        <div class="flex justify-center gap-6 mt-8 items-center">
          <!-- Tampilkan ikon Live Preview hanya jika liveLink tersedia -->
          <a v-if="project.liveLink" :href="project.liveLink" target="_blank"
             class="transition-all duration-300 hover:scale-110"
             title="Live Preview">
            <Icon name="uil:external-link-alt" size="32px" style="color: #1B2845" class="hover:opacity-70" />
          </a>

          <!-- Ikon GitHub selalu ditampilkan -->
          <a :href="project.githubLink" target="_blank"
             class="transition-all duration-300 hover:scale-110"
             title="View on GitHub">
            <Icon name="uil:github" size="32px" style="color: #1B2845" class="hover:opacity-70" />
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const projects = [
  {
    name: "Pomodor-Time",
    description: "Pomodoro Timer berbasis Node.js untuk meningkatkan produktivitas dengan teknik Pomodoro. Pengguna dapat mengatur durasi sesi kerja dan istirahat, serta menerima notifikasi setelah sesi selesai.",
    githubLink: "https://github.com/CHELVYN01/Pomodoro-Time--Node-js"
  },
  {
    name: "Ecommerce Catalog",
    description: "Menyelesaikan tugas sebagai Front-End Developer dalam program magang Core Initiative x Rakamin Academy di Home Credit Indonesia, mengembangkan keterampilan Vue.js dan soft skill sebagai developer.",
    githubLink: "https://www.rakamin.com/",
    liveLink: "https://ecommerce-catalog-black.vercel.app/"
  },
  {
    name: "Weather App",
    description: "Aplikasi cuaca berbasis web yang memungkinkan pengguna mencari informasi cuaca di berbagai lokasi secara real-time. Menampilkan suhu saat ini, kondisi cuaca, dan prakiraan cuaca untuk beberapa hari ke depan.",
    githubLink: "https://github.com/CHELVYN01/Weather-App",
    liveLink: "https://chelvyn01.github.io/Weather-App"
  }
];
</script>

<style>
/* Tambahkan animasi fade-in */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(15px);
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
