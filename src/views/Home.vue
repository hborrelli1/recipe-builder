<template>
  <div class="home">
    <AddRecipeForm v-on:add-recipe="addRecipe" />
    <Recipes v-bind:recipes="recipes" />
  </div>
</template>

<script>
import AddRecipeForm from '../components/AddRecipeForm';
import Recipes from '../components/Recipes';

export default {
  name: 'Home',
  components: {
    AddRecipeForm,
    Recipes
  },
  data() {
      return {
        recipes: [
          {
            id: 1,
            title: 'Chicken Parm',
            instructions: '1. Slow Cook chicken in crock pot. 2. Make sauce. 3. Combine and Enjoy.'
          },
          {
            id: 2,
            title: 'Chicken Noodle Soup',
            instructions: '1. Chop vegies. 2. Combine broth and chopped vegies into pot. 3. Heat on medium for 30 minutes.'
          },
          {
            id: 3,
            title: 'Stir Fry',
            instructions: '1. Chop vegies. 2. Heat oil in Wok then add in vegies. 3. Saute vegies and add seasoning. 4. Crack an egg in cook till done.'
          }
        ]
      }
    },
    methods: {
      addRecipe(newRecipe) {
        this.recipes = [...this.recipes, newRecipe]
      }
    }
}
</script>

<style scoped>
  .home {
    padding:0px 30px;
  }
</style>