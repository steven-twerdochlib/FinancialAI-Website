<template>
  <footer class="border-t border-gray-100 dark:border-gray-800">
    <div
      class="max-w-7xl mx-auto px-6 py-8 text-sm text-gray-600 dark:text-gray-400 flex flex-col md:flex-row justify-between items-center gap-2"
    >
      <div>© FinancialAI — Built for modern finance teams.</div>
      <div v-if="weatherInfo === ''">
        {{ currentDateTime }}
      </div>
      <div v-else>
        {{ currentDateTime }} · {{ weatherInfo }}
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  data() {
    return {
      currentDateTime: '',
      weatherInfo: 'Loading weather...',
    }
  },
  created() {
    this.updateDateTime()
    setInterval(this.updateDateTime, 60000) // update every minute
    this.fetchWeather()
  },
  methods: {
    updateDateTime() {
      const now = new Date()
      this.currentDateTime = now.toLocaleString([], {
        year: 'numeric',
        month: 'short',
        day: 'numeric',
        hour: '2-digit',
        minute: '2-digit',
      })
    },
    async fetchWeather() {
      try {
        // Example: using OpenWeatherMap API
        // Replace "YOUR_API_KEY" with your actual API key
        const response = await fetch(
          'https://api.openweathermap.org/data/2.5/weather?q=London&units=metric&appid=YOUR_API_KEY'
        )
        const data = await response.json()
        this.weatherInfo = `${data.main.temp}°C, ${data.weather[0].description}`
      } catch (error) {
        console.error('Error fetching weather:', error)
        this.weatherInfo = ''
      }
    }
  }
}
</script>

<style scoped>
/* optional footer styles */
</style>
