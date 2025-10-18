<template>
  <header class="fixed w-full top-0 left-0 z-50">
    <nav class="backdrop-blur-sm bg-white/60 dark:bg-gray-900 border-b border-gray-100 dark:border-gray-800">
      <div class="max-w-7xl mx-auto px-6 py-3 flex items-center justify-between">
        <div class="flex items-center gap-3">
          <div class="font-semibold text-lg">Financial<span class="text-cyan-500">AI</span></div>
          <ul class="hidden md:flex items-center gap-6 text-sm text-gray-700 dark:text-gray-200">
            <li class="hover:underline cursor-pointer">Our Product</li>
            <li class="hover:underline cursor-pointer">Benefits</li>
            <li class="hover:underline cursor-pointer">About Us</li>
            <li class="hover:underline cursor-pointer">Contact</li>
          </ul>
        </div>

        <div class="flex items-center gap-3">
          <button @click="toggleDarkMode" class="px-3 py-1 rounded-md border dark:border-gray-700">
            <span v-if="darkMode">🌙</span>
            <span v-else>☀️</span>
          </button>
          <a href="#" class="hidden md:inline-block px-4 py-2 rounded-lg bg-cyan-600 text-white">Get Started</a>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'Navbar',
  props: {
    darkMode: {
      type: Boolean,
      required: true
    }
  },
  methods: {
    toggleDarkMode() {
      this.$emit('toggleDarkMode')
    }
  }
}
</script>

<style scoped>
/* tiny adjustments */
</style>
