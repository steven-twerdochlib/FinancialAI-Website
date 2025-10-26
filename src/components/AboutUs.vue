<template>
  <section
    id="about"
    class="h-full bg-gray-50 dark:bg-gray-900 flex flex-col justify-center overflow-hidden"
  >
    <div
      class="max-w-5xl mx-auto px-4 sm:px-8 md:px-12 py-8 md:py-16 grid md:grid-cols-3 gap-12 items-center"
    >
      <!-- Left: CEO Image -->
      <div class="flex justify-center md:justify-start md:col-span-1">
        <img
          :src="ceoImage"
          alt="CEO portrait"
          class="w-48 h-48 object-cover rounded-full shadow-lg ring-4 ring-cyan-600/20 opacity-0 animate-fadeIn"
        />
      </div>

      <!-- Right: About text -->
      <div class="md:col-span-2 space-y-6">
        <!-- Title -->
        <h2 class="text-3xl sm:text-4xl md:text-5xl font-bold mb-6 opacity-0 animate-fadeIn">
          About 
          <span class="text-3xl sm:text-4xl md:text-5xl font-bold mb-6 opacity-0 animate-fadeIn">
            Financial<span class="text-cyan-500">AI</span>
          </span>
        </h2>

        <!-- Paragraphs -->
        <p class="text-gray-900 dark:text-gray-100 text-base sm:text-lg leading-relaxed opacity-0 animate-fadeIn">
          Founded with a vision to transform the financial industry through intelligent automation, we wanted to build a product to handle complex and repetitive financial processes,
          <span class="font-semibold text-black dark:text-white">
            Financial<span class="text-cyan-500">AI</span>
          </span> automates high-volume tasks, improves accuracy, and provides actionable insights at scale.
        </p>

        <p class="text-gray-900 dark:text-gray-100 text-base sm:text-lg leading-relaxed opacity-0 animate-fadeIn">
          Our AI-driven solutions integrate seamlessly into existing systems, helping organizations make faster, more confident financial decisions. Whether it’s automating reconciliations, generating forecasts, or improving audit accuracy — we aim to make finance effortless.
        </p>

        <p class="text-gray-900 dark:text-gray-100 text-base sm:text-lg leading-relaxed opacity-0 animate-fadeIn">
          At the heart of our mission is innovation and efficiency. Our automation solutions handle repetitive financial tasks at scale, allowing teams to focus on higher-value strategy and decision-making.
        </p>

        <!-- CEO Info -->
        <div class="flex items-center space-x-4 opacity-0 animate-fadeIn">
          <img
            :src="ceoImage"
            alt="CEO"
            class="w-14 h-14 object-cover rounded-full border-2 border-cyan-600"
          />
          <div>
            <h3 class="font-semibold text-lg">Adam Twerdochlib</h3>
            <p class="text-gray-500 dark:text-gray-400 text-sm">
              Founder & CEO, 
              <span class="font-semibold text-black dark:text-white">
                Financial<span class="text-cyan-500">AI</span>
              </span>
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import ceoImage from '../assets/defualt_ceo_icon.jpeg';

export default {
  name: 'AboutUs',
  data() {
    return {
      ceoImage,
      ceoName: 'Adam Twerdochlib',
      companyName: 'FinancialAI',
      companyMission:
        'Empowering financial professionals with AI-driven tools to automate workflows and make smarter decisions.',
    }
  },
}
</script>

<style scoped>
/* Fade-in animation for all elements */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}

.animate-fadeIn {
  animation: fadeIn 0.8s ease-in-out forwards;
}
</style>
