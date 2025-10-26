<template>
  <div :class="themeClass" class="min-h-screen flex flex-col transition-colors duration-300">
    <!-- Sticky Navbar -->
    <Navbar :darkMode="darkMode" @toggleDarkMode="toggleDarkMode" class="sticky top-0 z-50 h-[7vh]" />

    <!-- Hero Section fills remaining space -->
    <HeroSection class="h-[93vh]" />

    <Contact class="h-[93vh]"></Contact>
    <!-- Footer -->
    <Footer class="sticky bottom-0 h-[7vh]" />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import HeroSection from './components/HeroSection.vue'
import Footer from './components/Footer.vue'
import Contact from './components/Contact.vue'

export default {
  name: 'App',
  components: {
    Navbar,
    HeroSection,
    Footer,
    Contact
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
