<template>
  <header
    :class="[ $attrs.class, 'w-full fixed top-0 left-0 z-50 overflow-hidden' ]"
  >
    <nav
  class="h-full flex flex-wrap items-center justify-between md:justify-between justify-center 
         backdrop-blur-sm bg-white/60 dark:bg-gray-900 border-b border-gray-100 dark:border-gray-800 px-6 transition"
>

      <div
        class="max-w-7xl w-full mx-auto px-[1vh] sm:px-[2vh] md:px-[3vh] flex items-center justify-between"
      >
        <!-- Left Side -->
        <div class="flex items-center gap-[1.5vh]">
          <a
            href="#"
            class="font-semibold text-[2vh] sm:text-[2.3vh] md:text-[2.5vh] truncate"
          >
            Financial<span class="text-cyan-500">AI</span>
          </a>

          <ul class="flex flex-wrap items-center gap-[2vh] text-gray-700 dark:text-gray-200 text-[1.7vh]">

            <li class="hover:underline cursor-pointer">Our Product</li>
            <li class="hover:underline cursor-pointer">Benefits</li>
            <li class="hover:underline cursor-pointer">About Us</li>
            <li class="hover:underline cursor-pointer">
              <a href="#contact">Contact</a>
            </li>
          </ul>
        </div>

        <!-- Right Side -->
        <div class="flex items-center gap-[1vh]">
          <button
            @click="$emit('toggleDarkMode')"
            class="px-[1vh] py-[0.5vh] rounded-md border dark:border-gray-700 text-[1.6vh]"
          >
            <span v-if="darkMode">🌙</span>
            <span v-else>☀️</span>
          </button>

          <a
            href="#"
            class="md:inline-block px-[2vh] py-[1vh] rounded-lg bg-cyan-600 text-white text-[1.6vh] hover:bg-cyan-700 transition"
          >
            Get Started
          </a>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'Navbar',
  inheritAttrs: false,
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

<style>
html {
  scroll-behavior: smooth;
}
</style>
