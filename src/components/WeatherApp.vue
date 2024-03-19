<template>
    <div class="weather-app">
      <h1>Consulta el clima</h1>
      <input type="text"> // Aqui voy a ingresar la ciudad que luego vamos a pasar como solicitud
      <div v-if="loading">Cargando...</div>
      <div v-else>
        <div v-if="weather">
          <h2>{{ weather.name }}, {{ weather.sys.country }}</h2>
          <p>Temperatura: {{ weather.main.temp }}°C</p>
          <p>Velocidad del viento: {{ weather.wind.speed }} km</p>
        </div>
        <div v-else>
          <p>No se pudo obtener el clima</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        weather: null,
        loading: true,
        apiKey: '268df8bcf30eb52ad2201f3a78617bc9', 
        city: 'Tucuman' 
      };
    },
    mounted() {
      this.fetchWeather();
    },
    methods: {
      fetchWeather() {
        const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=${this.apiKey}`;
        fetch(apiUrl)
          .then(response => {
            if (!response.ok) {
              throw new Error('Network response was not ok');
            }
            return response.json();
          })
          .then(data => {
            this.weather = data;
            this.loading = false;
          })
          .catch(error => {
            console.error('Error fetching weather data:', error);
            this.loading = false;
          });
      }
    }
  };
  </script>
  
  <style scoped>
  .weather-app {
    text-align: center;
    margin-top: 50px;
  }
  </style>
  