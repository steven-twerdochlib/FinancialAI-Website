<template>
  <div :class="themeClass" class="min-h-screen flex flex-col transition-colors duration-300">
    <!-- Sticky Navbar -->
    <Navbar :darkMode="darkMode" @toggleDarkMode="toggleDarkMode" class="sticky top-0 z-50 h-[4rem]" />

    <!-- Hero Section fills remaining space -->
    <main :style="{ height: `calc(100vh - 4rem - 4rem)` }">
  <HeroSection class="h-full" />
</main>

    <!-- Footer -->
    <Footer class="h-[4rem]" />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import HeroSection from './components/HeroSection.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Navbar,
    HeroSection,
    Footer
  },
  data() {
    return {
      darkMode: false
    }
  },
  computed: {
    themeClass() {
      return this.darkMode ? 'dark bg-gray-900 text-white' : 'bg-white text-gray-900'
    }
  },
  methods: {
    toggleDarkMode() {
      this.darkMode = !this.darkMode
    }
  }
}
</script>

<style>
/* optional: smooth background image placement */
</style>
