<template>
  <footer
    v-bind="$attrs"
    class="w-full h-full bg-white dark:bg-gray-900 border-t border-gray-100 dark:border-gray-800 flex items-center justify-center overflow-hidden"
  >
    <div
      class="max-w-7xl w-full mx-auto px-[2vw] flex flex-col md:flex-row justify-between items-center gap-[1vh] text-[1.6vh]"
    >
      <div class="truncate">© FinancialAI — Built for modern finance teams.</div>
      
      <div v-if="weatherInfo === ''" class="truncate">
        {{ currentDateTime }}
      </div>
      <div v-else class="truncate">
        {{ currentDateTime }} · {{ weatherInfo }}
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer",
  inheritAttrs: false, // allows parent height to pass in
  data() {
    return {
      currentDateTime: "",
      weatherInfo: "Loading weather...",
    };
  },
  created() {
    this.updateDateTime();
    setInterval(this.updateDateTime, 60000); // update every minute
    this.fetchWeather();
  },
  methods: {
    updateDateTime() {
      const now = new Date();
      this.currentDateTime = now.toLocaleString([], {
        year: "numeric",
        month: "short",
        day: "numeric",
        hour: "2-digit",
        minute: "2-digit",
      });
    },
    async fetchWeather() {
      try {
        const response = await fetch(
          "https://api.openweathermap.org/data/2.5/weather?q=London&units=metric&appid=YOUR_API_KEY"
        );
        const data = await response.json();
        this.weatherInfo = `${data.main.temp}°C, ${data.weather[0].description}`;
      } catch (error) {
        console.error("Error fetching weather:", error);
        this.weatherInfo = "";
      }
    },
  },
};
</script>

<style scoped>
/* optional footer styles */
</style>
