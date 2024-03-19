<template>
  <div id="app">
    <WeatherApp />
  </div>
</template>

<script>
import WeatherApp from './components/WeatherApp.vue';

export default {
  name: 'App',
  components: {
    WeatherApp
  }
};
</script>

<style>
#app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
