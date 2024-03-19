<template>
  <div id="app">
    <WeatherApp />
    <header />
  </div>
</template>

<script>
import WeatherApp from './components/WeatherApp.vue';
import header from './components/header.vue';

export default {
  name: 'App',
  components: {
    WeatherApp,
    header
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
