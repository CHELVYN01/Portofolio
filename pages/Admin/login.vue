<template>
  <div
    class="min-h-screen bg-gradient-to-br from-gray-900 via-black to-gray-800 flex items-center justify-center p-4 relative overflow-hidden">
    <!-- Animated background elements -->
    <div class="absolute inset-0 overflow-hidden">
      <div
        class="absolute -top-4 -left-4 w-72 h-72 bg-green-500 rounded-full mix-blend-multiply filter blur-xl opacity-10 animate-pulse">
      </div>
      <div
        class="absolute -top-4 -right-4 w-72 h-72 bg-emerald-500 rounded-full mix-blend-multiply filter blur-xl opacity-10 animate-pulse delay-1000">
      </div>
      <div
        class="absolute -bottom-8 left-20 w-72 h-72 bg-teal-500 rounded-full mix-blend-multiply filter blur-xl opacity-10 animate-pulse delay-2000">
      </div>
    </div>

    <!-- Grid pattern background -->
    <div
      class="absolute inset-0 bg-[linear-gradient(rgba(34,197,94,0.03)_1px,transparent_1px),linear-gradient(90deg,rgba(34,197,94,0.03)_1px,transparent_1px)] bg-[size:32px_32px]">
    </div>

    <div class="relative z-10 w-full max-w-md">
      <!-- Logo/Brand Section -->
      <div class="text-center mb-8">
        <div
          class="inline-flex items-center justify-center w-16 h-16 bg-gradient-to-r from-green-500 to-emerald-500 rounded-2xl mb-4 shadow-lg shadow-green-500/25">
          <Icon name="heroicons:shield-check-solid" class="w-8 h-8 text-white" />
        </div>
        <h1 class="text-2xl font-bold text-white mb-2">
          Admin Dashboard
        </h1>
        <p class="text-gray-400 text-sm">
          Masuk ke panel administrasi
        </p>
      </div>

      <!-- Login Form -->
      <div class="bg-gray-800/50 backdrop-blur-xl rounded-2xl p-8 shadow-2xl border border-gray-700/50">
        <div class="space-y-6">
          <!-- Email Field -->
          <div class="space-y-2">
            <label for="email" class="text-sm font-medium text-gray-200 block">
              Email
            </label>
            <div class="relative">
              <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                <Icon name="heroicons:envelope-solid" class="h-5 w-5 text-gray-400" />
              </div>
              <input id="email" v-model="email" type="email"
                class="w-full pl-10 pr-4 py-3 bg-gray-700/50 border border-gray-600/50 rounded-xl text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-green-500 focus:border-transparent transition-all duration-200"
                placeholder="admin@example.com" required />
            </div>
          </div>

          <!-- Password Field -->
          <div class="space-y-2">
            <label for="password" class="text-sm font-medium text-gray-200 block">
              Password
            </label>
            <div class="relative">
              <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                <Icon name="heroicons:lock-closed-solid" class="h-5 w-5 text-gray-400" />
              </div>
              <input id="password" v-model="password" :type="showPassword ? 'text' : 'password'"
                class="w-full pl-10 pr-12 py-3 bg-gray-700/50 border border-gray-600/50 rounded-xl text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-green-500 focus:border-transparent transition-all duration-200"
                placeholder="••••••••" required />
              <button type="button" @click="togglePassword"
                class="absolute inset-y-0 right-0 pr-3 flex items-center text-gray-400 hover:text-white transition-colors duration-200">
                <Icon :name="showPassword ? 'heroicons:eye-slash-solid' : 'heroicons:eye-solid'" class="h-5 w-5" />
              </button>
            </div>
          </div>

          <!-- Remember Me & Forgot Password -->
          <div class="flex items-center justify-between">
            <div class="flex items-center">
              <input id="remember" v-model="remember" type="checkbox"
                class="h-4 w-4 text-green-500 bg-gray-700 border-gray-600 rounded focus:ring-green-500 focus:ring-2" />
              <label for="remember" class="ml-2 text-sm text-gray-300">
                Ingat saya
              </label>
            </div>
            <button type="button" class="text-sm text-green-400 hover:text-green-300 transition-colors duration-200"
              @click="forgotPassword">
              Lupa password?
            </button>
          </div>

          <!-- Login Button -->
          <button @click="handleLogin" :disabled="isLoading"
            class="w-full relative overflow-hidden bg-gradient-to-r from-green-500 to-emerald-500 text-white font-medium py-3 px-4 rounded-xl hover:from-green-600 hover:to-emerald-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-offset-2 focus:ring-offset-gray-800 disabled:opacity-50 disabled:cursor-not-allowed transition-all duration-200 group">
            <div class="flex items-center justify-center space-x-2">
              <div v-if="isLoading" class="w-5 h-5 border-2 border-white/30 border-t-white rounded-full animate-spin">
              </div>
              <span v-if="isLoading">Masuk...</span>
              <template v-else>
                <span>Masuk ke Dashboard</span>
                <Icon name="heroicons:arrow-right-solid"
                  class="w-4 h-4 group-hover:translate-x-1 transition-transform duration-200" />
              </template>
            </div>
          </button>
        </div>

        <!-- Additional Info -->
        <div class="mt-6 pt-6 border-t border-gray-700/50">
          <p class="text-center text-xs text-gray-400">
            Hanya untuk administrator yang berwenang
          </p>
        </div>
      </div>

      <!-- Footer -->
      <div class="text-center mt-8">
        <p class="text-xs text-gray-500">
          © 2025 CheivynKleden. All rights reserved.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
// Page meta
useHead({
  title: 'Admin Login - Dashboard',
  meta: [
    { name: 'description', content: 'Admin login page for dashboard access' },
    { name: 'robots', content: 'noindex' }
  ]
})

// Reactive data
const email = ref('')
const password = ref('')
const remember = ref(false)
const showPassword = ref(false)
const isLoading = ref(false)

// Methods
const togglePassword = () => {
  showPassword.value = !showPassword.value
}

const handleLogin = async () => {
  // Basic validation
  if (!email.value || !password.value) {
    // You can use Nuxt's built-in notification or a toast library
    alert('Mohon isi email dan password')
    return
  }

  isLoading.value = true

  try {
    // Replace this with your actual authentication logic
    // Example using $fetch (Nuxt 3's built-in fetch)
    /*
    const response = await $fetch('/api/auth/login', {
      method: 'POST',
      body: {
        email: email.value,
        password: password.value,
        remember: remember.value
      }
    })

    // Handle successful login
    if (response.success) {
      // Store token in cookies or localStorage
      const token = useCookie('auth-token')
      token.value = response.token
      
      // Redirect to dashboard
      await navigateTo('/admin/dashboard')
    }
    */

    // Demo simulation
    await new Promise(resolve => setTimeout(resolve, 2000))

    // Show success message
    alert('Login berhasil! (Demo mode)')

    // In real app, redirect to dashboard
    // await navigateTo('/admin/dashboard')

  } catch (error) {
    console.error('Login error:', error)
    alert('Login gagal. Silakan coba lagi.')
  } finally {
    isLoading.value = false
  }
}

const forgotPassword = () => {
  // Navigate to forgot password page or show modal
  alert('Fitur lupa password akan segera tersedia')
  // await navigateTo('/admin/forgot-password')
}

// Lifecycle
onMounted(() => {
  // Check if user is already logged in
  const token = useCookie('auth-token')
  if (token.value) {
    // Redirect to dashboard if already authenticated
    // navigateTo('/admin/dashboard')
  }
})
</script>

<style scoped>
/* Custom animations and styles */
@keyframes pulse {

  0%,
  100% {
    opacity: 0.1;
  }

  50% {
    opacity: 0.2;
  }
}

.animate-pulse {
  animation: pulse 4s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

.delay-1000 {
  animation-delay: 1s;
}

.delay-2000 {
  animation-delay: 2s;
}

/* Input focus effects */
input:focus {
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(34, 197, 94, 0.15);
}

/* Button hover effects */
button:hover:not(:disabled) {
  transform: translateY(-1px);
  box-shadow: 0 8px 25px rgba(34, 197, 94, 0.3);
}

/* Smooth transitions */
* {
  transition-property: all;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}
</style>