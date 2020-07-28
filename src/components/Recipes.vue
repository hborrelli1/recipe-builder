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
        v-on:del-recipe="$emit('del-recipe', recipe.id)"
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
  header {
    text-align:center;
    padding-top:20px;
    border-bottom:1px solid #000;
    margin-bottom:20px;
  }

  .recipes-list {
    display: flex;
    flex-flow:wrap;
    justify-content: flex-start;
  }

</style>