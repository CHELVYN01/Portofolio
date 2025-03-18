<template>
  <!-- Hero Section -->
  <section
  id="hero"
    class="h-screen flex flex-col justify-center items-center text-center px-4 pt-16 bg-gradient-to-t from-black via-[#000301] to-[#000A03] text-white relative overflow-hidden"
  >
    <div class="absolute inset-0 bg-opacity-20 flex justify-center items-center animate-pulse">
      <div class="w-48 h-48 bg-green-500 opacity-20 rounded-full blur-3xl"></div>
    </div>

    <h1 class="text-5xl font-bold uppercase text-[#0F3D20] animate-fade-in">
      <span class="text-green-500">Hello, I'm Blasius Chelvyn Kera Kleden</span>
    </h1>
    
    <p class="mt-6 text-xl text-gray-300 max-w-3xl text-center animate-slide-up">
      A passionate <span class="text-green-500 font-semibold">Front-End Developer & UI/UX Designer</span>  
      dedicated to crafting seamless user experiences with clean and modern design.  
      I specialize in building responsive, high-performance web applications using  
      cutting-edge technologies like Vue.js, React, and Next.js.
    </p>
    
    
  </section>
</template>

<style scoped>
@keyframes fade-in {
  from { opacity: 0; transform: translateY(-10px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes slide-up {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.animate-fade-in {
  animation: fade-in 1s ease-out;
}

.animate-slide-up {
  animation: slide-up 1s ease-out 0.5s forwards;
}
</style>