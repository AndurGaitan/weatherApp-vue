<template>
    <div class="weather-app">
      <h1>Consulta el clima</h1>
      <div>
        <label for="city">Ciudad:</label>
        <input type="text" id="city" v-model="city" @keydown.enter="searchWeather">
        <button @click="searchWeather">Buscar</button>
      </div>
      <div v-if="loading">Cargando...</div>
      <div v-else>
          <div v-for="(result, index) in weatherResults" :key="index" class="weather-card">
            <h2>{{ result.name }}, {{ result.sys.country }}</h2>
            <p>Temperatura: {{ result.main.temp }}°C</p>
          </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        weatherResults: [],
        loading: true,
        apiKey: '268df8bcf30eb52ad2201f3a78617bc9', 
        city: 'Tucuman' 
      };
    },
    methods: {
      searchWeather() {
        if (this.city.trim() === '') {
        return; 
        }
        this.loading = true;
        const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=${this.apiKey}`;
        fetch(apiUrl)
          .then(response => {
            if (!response.ok) {
              throw new Error('Error en la respuesta');
            }
            return response.json();
          })
          .then(data => {
            this.weatherResults.push(data);
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
  input[type="text"]{
    margin-right: 10px;
  }
  .weather-card {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;
  margin-bottom: 10px;
}
  </style>
  