  <template>
    <!-- Chat for Project Section -->
    <section id="chat-project" class="py-16 px-6 text-center bg-black text-white">
      <h2 class="text-4xl font-bold text-green-400">Let's Build Your Project</h2>
      <p class="mt-3 text-gray-400">Tell us about your idea, and let's bring it to life together.</p>

      <form @submit.prevent="startChat" class="mt-6 max-w-lg mx-auto flex flex-col gap-4 bg-[#0A1B2F] shadow-md rounded-xl p-6 border border-green-500">
        <input
          v-model="name"
          type="text"
          placeholder="Your Name"
          class="p-4 bg-transparent border border-gray-600 rounded-lg text-white outline-none focus:border-green-400"
        />
        <input
          v-model="project"
          type="text"
          placeholder="Describe Your Project"
          class="p-4 bg-transparent border border-gray-600 rounded-lg text-white outline-none focus:border-green-400"
        />
        <button 
          type="submit"
          class="bg-green-500 text-black px-6 py-4 font-medium rounded-lg transition duration-300 hover:bg-green-600 hover:text-white">
          🚀 Chat Now
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
