<template>
  <section v-bind="$attrs" class="relative flex items-center justify-start overflow-hidden">
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
    <div class="relative z-10 max-w-[80vw] pl-[6vw] space-y-[2vh]">
      <h1 class="font-extrabold leading-tight text-[5vh] md:text-[6vh]">
        Empowering Finance with AI
      </h1>
      <p class="text-[2.3vh] text-gray-600 dark:text-gray-300 max-w-[60vw] leading-relaxed">
        Transform your customer service with our Smart AI Assistance Chatbot.
        Let our AI handle invoice queries, payments, and disputes — so your team
        can focus on what matters.
      </p>

      <div class="flex gap-[2vw] pt-[2vh]">
        <button
          class="px-[3vw] py-[1.5vh] rounded-[1vh] bg-cyan-600 text-white font-medium text-[2vh] hover:bg-cyan-700 transition-colors duration-200"
        >
          See Product
        </button>
        <button
          @click="scrollToContact"
          class="px-[3vw] py-[1.5vh] rounded-[1vh] bg-gray-200 dark:bg-gray-700 text-gray-900 dark:text-white font-medium text-[2vh] hover:bg-gray-300 dark:hover:bg-gray-600 transition-colors duration-200"
        >
          Request A Demo
        </button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "HeroSection",
  inheritAttrs: false,
  methods: {
    scrollToContact() {
      const contact = document.querySelector("#contact");
      if (contact) contact.scrollIntoView({ behavior: "smooth" });
    },
  },
};
</script>


<style scoped>
/* Ensure text remains readable on smaller screens */
@media (max-width: 640px) {
  .pl-10 { padding-left: 1rem; }
}
</style>
