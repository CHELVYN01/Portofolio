<template>
  <section id="skills" class="py-20 px-6 bg-[#F5F1E8] text-[#1B2845] border-t-2 border-[#D4C5B0]">
    <!-- Section Header -->
    <div class="text-center mb-12">
      <h2 class="text-5xl font-bold text-[#1B2845] mb-4">My Skills</h2>
      <div class="w-24 h-1 bg-[#C9A961] mx-auto mb-4"></div>
      <p class="text-[#4A4A4A] text-lg">Technologies and tools I work with</p>
    </div>

    <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-6 mt-12 max-w-5xl mx-auto">
      <div
        v-for="(skill, index) in skills"
        :key="index"
        class="group flex flex-col items-center justify-center p-6 bg-[#FAF8F3] border-2 border-[#D4C5B0] shadow-sm transition-all duration-300 hover:border-[#C9A961] hover:-translate-y-1 hover:shadow-md cursor-pointer animate-fade-in"
        :style="{ animationDelay: `${index * 0.1}s` }"
      >
        <Icon :name="skill.icon" class="text-4xl transition-all group-hover:scale-110" />
        <span class="mt-3 text-sm font-semibold text-[#1B2845] transition-all">{{ skill.name }}</span>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Icon } from '#components';

const skills = [
  { name: "Java", icon: "vscode-icons:file-type-java"},
  { name: "Python", icon: "vscode-icons:file-type-python"},
  { name: "PHP", icon: "vscode-icons:file-type-php" },
  { name: "JavaScript", icon:"vscode-icons:file-type-js-official" },
  { name: "Next.js", icon: "vscode-icons:file-type-light-next" },
  { name: "React.js", icon: "vscode-icons:file-type-reactjs"},
  { name: "Vue.js", icon: "vscode-icons:file-type-vue" },
  { name: "Nuxt.js", icon: "vscode-icons:file-type-nuxt" },
  { name: "CodeIgniter", icon: "uil:fire" },
  { name: "Tailwind CSS", icon:"vscode-icons:file-type-tailwind" }
];
</script>


<style>
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px) scale(0.9);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

.animate-fade-in {
  animation: fadeIn 0.5s ease-out forwards;
}
</style>
