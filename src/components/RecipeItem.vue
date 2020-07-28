<template>
  <div class="recipe-item">
    <h4>{{ recipe.title }}</h4>
    <p>{{ recipe.instructions }}</p>
  </div>
</template>

<script>
  export default {
    name: 'RecipeItem',
    props: ['recipe']
  }
</script>

<style scoped>
  .recipe-item {
    width:33.3%;
  }
</style>