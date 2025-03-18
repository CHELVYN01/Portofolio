<template>
  <section id="skills" class="py-16 px-6 bg-[#000A03] text-white">
    <h2 class="text-4xl font-bold text-center text-[#5FF573] mb-6">MY SKILLS</h2>

    <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-6 mt-6 max-w-4xl mx-auto">
      <div 
        v-for="(skill, index) in skills" 
        :key="index" 
        class="group flex flex-col items-center justify-center p-5 bg-[#0A1B2F] rounded-lg shadow-md transition-all duration-300 hover:bg-[#123456] hover:scale-105 hover:shadow-lg cursor-pointer animate-fade-in"
        :style="{ animationDelay: `${index * 0.1}s` }"
      >
        <Icon :name="skill.icon" class="text-3xl text-[#5FF573] group-hover:text-white transition-all" />
        <span class="mt-2 text-sm font-semibold text-[#BFFFC2] group-hover:text-white transition-all">{{ skill.name }}</span>
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
