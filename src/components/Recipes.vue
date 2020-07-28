<template>
  <section>
    <header>
      <h3>Recipes:</h3>
    </header>
    <div 
      class='recipes-list'
      v-for='recipe in recipes'
      v-bind:key='recipe.id'
    >
    </div>
  </section>
</template>

<script>
  export default {
    name: 'Recipes',
    props: ['recipes']
  }
</script>

<style scoped>

</style>