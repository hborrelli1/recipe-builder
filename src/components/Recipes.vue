<template>
  <section>
    <header>
      <h3>Recipes:</h3>
    </header>
    <div class='recipes-list'>
      <RecipeItem 
        v-for='recipe in recipes'
        v-bind:key='recipe.id'
        v-bind:recipe='recipe'
      />
    </div>
  </section>
</template>

<script>
  import RecipeItem from './RecipeItem'

  export default {
    name: 'Recipes',
    components: {
      RecipeItem
    },
    props: ['recipes']
  }
</script>

<style scoped>
  .recipes-list {
    display: flex;
    flex-flow:wrap;
  }
</style>