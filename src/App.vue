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
    WeatherApp,
  }
};
</script>

<style>
#app {
  font-family: Roboto;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
