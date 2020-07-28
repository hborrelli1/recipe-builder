<template>
  <header>
    <h1>Recipe Builder</h1>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
  export default {
    name: 'Header'
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
  }
</style>