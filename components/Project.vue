<template>
  <!-- Projects Section -->
  <section id="projects" class="py-16 px-6 bg-gradient-to-b from-black via-[#000301] to-[#000A03] text-white">
    <h2 class="text-4xl font-bold text-center text-green-400">My Projects</h2>
    <p class="text-center text-gray-300 mt-2">Check out some of my recent work</p>

    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-8 mt-10 max-w-5xl mx-auto">
      <div v-for="(project, index) in projects" :key="index"
        class="p-6 bg-[#0A1B2F] rounded-xl shadow-lg text-center transition duration-300 hover:shadow-2xl hover:scale-105">
        <h3 class="text-2xl font-semibold text-green-300">{{ project.name }}</h3>
        <p class="mt-2 text-gray-400 text-sm">{{ project.description }}</p>

        <div class="flex justify-center gap-4 mt-6 items-center">
          <!-- Tampilkan ikon Live Preview hanya jika liveLink tersedia -->
          <a v-if="project.liveLink" :href="project.liveLink" target="_blank">
            <Icon name="uil:external-link-alt" size="30px" style="color: white" />
          </a>

          <!-- Ikon GitHub selalu ditampilkan -->
          <a :href="project.githubLink" target="_blank" class="text-gray-300 hover:text-gray-500">
            <Icon name="uil:github" size="32px" style="color: white" />
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
