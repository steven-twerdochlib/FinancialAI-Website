<template>
  <section class="relative flex items-center">
    <!-- Background image -->
    <div class="absolute inset-0 overflow-hidden">
      <img
        src="/src/assets/hero-spreadsheet.png"
        class="absolute inset-0 w-full h-full object-cover object-right transform rotate-12 blur-[3px] scale-125"
      />
      <div
        class="absolute inset-0 bg-gradient-to-r from-white/50 via-white/30 to-transparent dark:from-gray-900 dark:via-gray-900/85 dark:to-transparent"
      ></div>
    </div>

    <!-- Hero content -->
    <div class="relative z-10 max-w-3xl pl-10 md:pl-20">
      <h1 class="text-4xl md:text-6xl font-extrabold leading-tight">
        Empowering Finance with AI
      </h1>
      <p class="mt-4 text-lg md:text-xl text-gray-600 dark:text-gray-300 max-w-xl">
        Transform your customer service with our Smart AI Assistance Chatbot. Let our AI handle invoice queries, payments, and disputes — so your team can focus on what matters.
      </p>

      <div class="mt-8 flex gap-4">
        <button class="px-6 py-3 rounded-lg bg-cyan-600 text-white font-medium hover:bg-cyan-700 transition-colors duration-200">
          See Product
        </button>
        <button @click="scrollToContact" class="px-6 py-3 rounded-lg bg-gray-200 dark:bg-gray-700 text-gray-900 dark:text-white font-medium hover:bg-gray-300 dark:hover:bg-gray-600 transition-colors duration-200">
          Request A Demo
        </button>
      </div>
    </div>
  </section>
</template>


<script>
export default {
  name: 'HeroSection',
  methods: {
    scrollToContact() {
      const contactSection = document.getElementById('contact')
      if (contactSection) {
        contactSection.scrollIntoView({ behavior: 'smooth' })
      }
    }
  }
}
</script>

<style scoped>
/* Ensure text remains readable on smaller screens */
@media (max-width: 640px) {
  .pl-10 { padding-left: 1rem; }
}
</style>
