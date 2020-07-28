<template>
  <div id="app">
    <Header />
    <router-view/>
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

  #nav {
    padding: 30px;
  }

  #nav a {
    font-weight: bold;
    color: #f4f4f4;
  }

  #nav a.router-link-exact-active {
    color: #42b983;
  }
</style>
