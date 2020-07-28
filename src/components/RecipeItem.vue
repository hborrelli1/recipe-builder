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
    width:32%;
    padding:20px;
    background-color:#f4f4f4;
    margin-right:2%;
    margin-bottom:20px;
  }
  
  .recipe-item:nth-of-type(3n) {
    margin-right:0px;
  }
</style>