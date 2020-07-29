<template>
  <div class="home">
    <AddRecipeForm v-on:add-recipe="addRecipe" />
    <Recipes 
      v-bind:recipes="recipes" 
      v-on:del-recipe="deleteRecipe"
    />
  </div>
</template>

<script>
import AddRecipeForm from '../components/AddRecipeForm';
import Recipes from '../components/Recipes';
import defaultRecipes from '../default-recipes/recipes.js';

console.log(defaultRecipes);
export default {
  name: 'Home',
  components: {
    AddRecipeForm,
    Recipes
  },
  data() {
      return {
        recipes: defaultRecipes,
        searchQuery: ''
      }
    },
    methods: {
      addRecipe(newRecipe) {
        this.recipes = [...this.recipes, newRecipe];
      },
      deleteRecipe(id) {
        this.recipes = this.recipes.filter(recipe => recipe.id !== id);
      }
    }
}
</script>

<style scoped>
  .home {
    /* padding:0px 50px; */
    width:100%;
    max-width:1200px;
    margin:0 auto;
  }
</style>