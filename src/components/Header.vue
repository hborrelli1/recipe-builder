<template>
  <header>
    <h1>Recipe Builder</h1>
    <div id="nav">
      <router-link to="/" v-if="isNotHomepage()" >Home</router-link>
      <!-- <router-link to="/about">About</router-link> -->
    </div>
  </header>
</template>

<script>
  export default {
    name: 'Header',
    methods: {
      isNotHomepage() {
        return this.$route.fullPath !== '/';
      }
    }
  }
</script>

<style scoped>
  header {
    background-color:#333;
    color:#f4f4f4;
    display: flex;
    flex-direction:column;
    align-items:center;
    justify-content: center;
    padding:20px;
  }

  #nav {
    padding: 10px;
  }

  #nav a {
    font-weight: bold;
    color: #f4f4f4;
    text-decoration:none;
  }

  #nav a:hover {
    text-decoration:underline;
  }

  #nav a.router-link-exact-active {
    color: #42b983;
  }
</style>