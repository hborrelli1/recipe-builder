<template>
  <div id="app">
    <Header />
    <router-view :key="$route.fullPath" />
  </div>
</template>

<script>
  import Header from './components/Header';

  export default {
    name: 'app',
    components: {
      Header,
    }
  }
</script>

<style>
  * {
    box-sizing: border-box;
    margin:0;
    padding:0;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
</style>
