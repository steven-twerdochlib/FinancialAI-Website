<template>
  <header :class="[$attrs.class, 'w-full fixed top-0 left-0 z-50 overflow-visible']">
    <nav
      class="h-full flex items-center justify-between px-[3vw] md:px-[6vw] bg-white/60 dark:bg-gray-900 border-b border-gray-100 dark:border-gray-800"
    >
      <!-- Left: Hamburger + Logo -->
      <div class="flex items-center gap-[1vw]">
        <!-- Hamburger only on mobile -->
        <button class="md:hidden text-[3vh]" @click="mobileOpen = !mobileOpen">☰</button>
        <!-- Logo -->
        <a href="#" @click.prevent="scrollTo('#hero')" class="font-semibold text-[3.5vh] sm:text-[4vh] md:text-[4.5vh]">
          Financial<span class="text-cyan-500">AI</span>
        </a>
      </div>

      <!-- Desktop links -->
      <ul
  class="hidden md:flex flex-wrap items-center gap-[2vw] text-gray-700 dark:text-gray-200"
  style="font-size: 2.2vh"
>
  <li @click.prevent="scrollTo('#contact')" class="hover:underline cursor-pointer">Our Product</li>
  <li @click.prevent="scrollTo('#contact')" class="hover:underline cursor-pointer">Benefits</li>
  <li @click.prevent="scrollTo('#AboutUs')" class="hover:underline cursor-pointer">About Us</li>
  <li @click.prevent="scrollTo('#contact')" class="hover:underline cursor-pointer"><a href="#contact">Contact</a></li>
</ul>

      <!-- Right buttons -->
      <div class="flex items-center gap-[1vw]">
        <button @click="$emit('toggleDarkMode')" class="px-[1vw] py-[0.5vh] rounded-md border dark:border-gray-700 text-[2vh]">
          <span v-if="darkMode">🌙</span>
          <span v-else>☀️</span>
        </button>
        <a
          href="#"
          class="hidden md:inline-block px-[2vw] py-[1vh] rounded-lg bg-cyan-600 text-white text-[2vh] hover:bg-cyan-700 transition"
        >
          Get Started
        </a>
      </div>
    </nav>

    <!-- Mobile dropdown -->
    <transition name="fade">
      <div
        v-if="mobileOpen"
        class="md:hidden flex flex-col bg-white dark:bg-gray-900 text-gray-700 dark:text-gray-200 py-[1vh] px-[4vw] border-t border-gray-200 dark:border-gray-800 z-50 absolute w-full"
      >
        <a href="#" @click.prevent="scrollTo('#contact')" class="py-2 w-full hover:underline" @click="closeMobileMenu">Our Product</a>
        <a href="#" @click.prevent="scrollTo('#contact')" class="py-2 w-full hover:underline" @click="closeMobileMenu">Benefits</a>
        <a href="#" @click.prevent="scrollTo('#contact')" class="py-2 w-full hover:underline" @click="closeMobileMenu">About Us</a>
        <a href="#contact" @click.prevent="scrollTo('#contact')" class="py-2 w-full hover:underline" @click="closeMobileMenu">Contact</a>
      </div>
    </transition>
  </header>
</template>

<script>
export default {
  name: 'Navbar',
  inheritAttrs: false,
  props: {
    darkMode: { type: Boolean, required: true }
  },
  data() {
    return {
      mobileOpen: false
    }
  },
  methods: {
    toggleDarkMode() {
      this.$emit('toggleDarkMode')
    },
    closeMobileMenu() {
      this.mobileOpen = false
    },
    scrollTo(selector) {
  const el = document.querySelector(selector);
  if (el) {
    // Get element's top position relative to the document
    const top = el.getBoundingClientRect().top + window.pageYOffset;

    // Scroll to slightly above the element (offset in pixels)
    const offset = 65; // adjust this value as needed
    window.scrollTo({
      top: top - offset,
      behavior: 'smooth'
    });
  }
  this.closeMobileMenu();
}
  }
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
