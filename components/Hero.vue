<template>
  <!-- Hero Section -->
  <section id="hero"
    class="h-screen flex flex-col justify-center items-center text-center px-8 pt-16 bg-[#F5F1E8] text-[#1B2845] relative overflow-hidden">

    <!-- Classic Decorative Border -->
    <div class="absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-transparent via-[#C9A961] to-transparent"></div>
    <div class="absolute bottom-0 left-0 right-0 h-1 bg-gradient-to-r from-transparent via-[#C9A961] to-transparent"></div>

    <!-- Classic Ornamental Corners -->
    <div class="absolute top-20 left-8 w-24 h-24 border-t-4 border-l-4 border-[#C9A961] opacity-30"></div>
    <div class="absolute top-20 right-8 w-24 h-24 border-t-4 border-r-4 border-[#C9A961] opacity-30"></div>
    <div class="absolute bottom-20 left-8 w-24 h-24 border-b-4 border-l-4 border-[#C9A961] opacity-30"></div>
    <div class="absolute bottom-20 right-8 w-24 h-24 border-b-4 border-r-4 border-[#C9A961] opacity-30"></div>

    <!-- Content -->
    <div class="max-w-4xl z-10">
      <div class="mb-6 text-[#C9A961] text-sm font-semibold tracking-[0.3em] uppercase animate-fade-in">Welcome to my Portfolio</div>

      <h1 class="text-6xl md:text-7xl font-bold text-[#1B2845] mb-4 animate-fade-in leading-tight">
        Blasius Chelvyn Kera Kleden
      </h1>

      <div class="w-32 h-1 bg-[#C9A961] mx-auto my-8"></div>

      <p class="mt-8 text-xl md:text-2xl text-[#4A4A4A] max-w-3xl mx-auto leading-relaxed animate-slide-up">
        A versatile <span class="text-[#C9A961] font-semibold italic">Fullstack Developer & Odoo Developer</span>
        passionate about building modern web applications and robust business solutions.
        I specialize in crafting responsive front-end interfaces, scalable back-end systems,
        and customizing Odoo to streamline workflows and boost efficiency.
      </p>

      <!-- Classic Button -->
      <div class="mt-12 animate-slide-up">
        <a href="#projects" class="inline-block bg-[#1B2845] text-[#FAF8F3] px-8 py-3 border-2 border-[#1B2845] hover:bg-[#C9A961] hover:border-[#C9A961] hover:text-[#1B2845] transition-all duration-300 font-semibold tracking-wide">
          View My Work
        </a>
      </div>
    </div>

  </section>
</template>

<style scoped>
@keyframes fade-in {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slide-up {
  from {
    opacity: 0;
    transform: translateY(20px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in {
  animation: fade-in 1s ease-out;
}

.animate-slide-up {
  animation: slide-up 1s ease-out 0.5s forwards;
}
</style>