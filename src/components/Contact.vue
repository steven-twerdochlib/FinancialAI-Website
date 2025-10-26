<template>
  <section
  id="contact"
  class="h-full bg-gray-50 dark:bg-gray-900 flex flex-col justify-center overflow-hidden"
>
    <div
  class="flex-1 overflow-auto max-w-5xl mx-auto px-4 sm:px-8 md:px-12 py-8 md:py-12"
>
      <h2 class="text-2xl sm:text-3xl md:text-4xl font-bold text-center mb-6 sm:mb-10">
  Get in Touch
</h2>

<p class="text-center text-gray-600 dark:text-gray-400 max-w-2xl mx-auto mb-8 sm:mb-12 text-sm sm:text-base md:text-lg">
  Have a question, want a demo, or want to learn how FinancialAI can transform your financial workflows?  
  Send us a message — we’ll get back to you soon.
</p>

      <form
  @submit.prevent="handleSubmit"
  class="bg-white dark:bg-gray-800 shadow-lg rounded-2xl p-6 sm:p-8 md:p-10 space-y-4 sm:space-y-6 flex-1 overflow-auto"
>
        <div class="grid md:grid-cols-2 gap-6">
          <div>
            <label for="name" class="block mb-2 font-medium">Name</label>
            <input
              v-model="form.name"
              id="name"
              type="text"
              required
              class="w-full px-4 py-3 rounded-lg border border-gray-300 dark:border-gray-700 dark:bg-gray-900 focus:outline-none focus:ring-2 focus:ring-cyan-500"
            />
          </div>

          <div>
            <label for="email" class="block mb-2 font-medium">Email</label>
            <input
              v-model="form.email"
              id="email"
              type="email"
              required
              class="w-full px-4 py-3 rounded-lg border border-gray-300 dark:border-gray-700 dark:bg-gray-900 focus:outline-none focus:ring-2 focus:ring-cyan-500"
            />
          </div>
        </div>

        <div>
          <label for="message" class="block mb-2 font-medium">Message</label>
          <textarea
            v-model="form.message"
            id="message"
            rows="5"
            required
            class="w-full px-4 py-3 rounded-lg border border-gray-300 dark:border-gray-700 dark:bg-gray-900 focus:outline-none focus:ring-2 focus:ring-cyan-500"
          ></textarea>
        </div>

        <div class="flex justify-end">
          <button
            type="submit"
            class="px-6 py-3 bg-cyan-600 text-white rounded-lg font-medium hover:bg-cyan-700 transition"
          >
            Send Message
          </button>
        </div>

        <p v-if="submitted" class="text-green-600 dark:text-green-400 text-sm mt-4">
          ✅ Thanks for reaching out! We’ll get back to you shortly.
        </p>
      </form>

      <!-- Social Links -->
      <div class="flex flex-wrap justify-center mt-6 sm:mt-10 space-x-6 sm:space-x-8">
        <!-- LinkedIn -->
        <button
          @click="openLinkedIn"
          rel="noopener"
          class="hover:opacity-80 transition"
          aria-label="LinkedIn"
        >
          <i class="fa-brands fa-linkedin fa-2x" style="color: #0A66C2;"></i>
        </button>

        <!-- Gmail -->
        <button
          @click="openEmail"
          class="hover:opacity-80 transition"
          aria-label="Email"
        >
          <i class="fa-solid fa-envelope fa-2x" style="color: #EA4335;"></i>
        </button>
      </div>
    </div>
  </section>
</template>

<script>
import emailjs from 'emailjs-com'
import '@fortawesome/fontawesome-free/css/all.min.css'

export default {
  name: 'Contact',
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      },
      submitted: false,
      contactEmail: import.meta.env.VITE_CONTACT_EMAIL,
      linkedInAddress: import.meta.env.VITE_LINKEDIN_ADDRESS
    }
  },
  methods: {
    async handleSubmit() {
      try {
        const serviceID = import.meta.env.VITE_SERVICE_ID
        const templateID = import.meta.env.VITE_TEMPLATE_ID
        const publicKey = import.meta.env.VITE_PUBLIC_KEY

        await emailjs.send(serviceID, templateID, this.form, publicKey)
        this.submitted = true
        this.form = { name: '', email: '', message: '' }
        setTimeout(() => (this.submitted = false), 5000)
      } catch (err) {
        console.error('EmailJS error:', err)
      }
    },
    openLinkedIn() {
      const linkedIn = import.meta.env.VITE_LINKEDIN_ADDRESS;
      window.open(linkedIn, "_blank");
    },
    openEmail() {
      const email = import.meta.env.VITE_CONTACT_EMAIL;
      const url = `https://mail.google.com/mail/?view=cm&to=${email}`;
      window.open(url, "_blank");
    }
  }
}
</script>

<style scoped>
/* optional: center icons on small screens */
a i {
  transition: transform 0.2s ease;
}
a:hover i {
  transform: scale(1.15);
}
</style>
