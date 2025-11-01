<template>
  <!-- Chat for Project Section -->
  <section id="chat-project" class="py-20 px-6 text-center bg-[#F5F1E8] text-[#1B2845] border-t-2 border-[#D4C5B0]">
    <!-- Section Header -->
    <div class="mb-12">
      <h2 class="text-5xl font-bold text-[#1B2845] mb-4">Let's Build Your Project</h2>
      <div class="w-24 h-1 bg-[#C9A961] mx-auto mb-4"></div>
      <p class="mt-3 text-[#4A4A4A] text-lg">Tell us about your idea, and let's bring it to life together.</p>
    </div>

    <form @submit.prevent="startChat" class="mt-8 max-w-xl mx-auto flex flex-col gap-6 bg-[#FAF8F3] shadow-lg p-10 border-4 border-[#C9A961] relative">
      <!-- Decorative Corner Elements -->
      <div class="absolute top-0 left-0 w-6 h-6 border-t-2 border-l-2 border-[#1B2845]"></div>
      <div class="absolute top-0 right-0 w-6 h-6 border-t-2 border-r-2 border-[#1B2845]"></div>
      <div class="absolute bottom-0 left-0 w-6 h-6 border-b-2 border-l-2 border-[#1B2845]"></div>
      <div class="absolute bottom-0 right-0 w-6 h-6 border-b-2 border-r-2 border-[#1B2845]"></div>

      <input
        v-model="name"
        type="text"
        placeholder="Your Name"
        class="p-4 bg-[#F5F1E8] border-2 border-[#D4C5B0] text-[#1B2845] outline-none focus:border-[#C9A961] transition-colors duration-300"
      />
      <input
        v-model="project"
        type="text"
        placeholder="Describe Your Project"
        class="p-4 bg-[#F5F1E8] border-2 border-[#D4C5B0] text-[#1B2845] outline-none focus:border-[#C9A961] transition-colors duration-300"
      />
      <button
        type="submit"
        class="bg-[#1B2845] text-[#FAF8F3] px-8 py-4 font-semibold border-2 border-[#1B2845] transition-all duration-300 hover:bg-[#C9A961] hover:border-[#C9A961] hover:text-[#1B2845] tracking-wide">
        Start Conversation
      </button>
    </form>
  </section>
</template>

  <script setup>
  import { ref } from "vue";

  const name = ref("");
  const project = ref("");

  const startChat = () => {
    if (!name.value || !project.value) {
      alert("Please fill in all fields!");
      return;
    }

    // WhatsApp Chat Link (Replace with your own number)
    const whatsappNumber = "6281234567890";
    const message = `Hello, my name is ${name.value}. I want to discuss a project: ${project.value}`;
    const encodedMessage = encodeURIComponent(message);
    window.open(`https://wa.me/${whatsappNumber}?text=${encodedMessage}`, "_blank");
  };
  </script>
