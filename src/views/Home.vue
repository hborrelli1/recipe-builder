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
            title: 'Banana and Blueberry French Toast',
            instructions: '1. Beat egg, vanilla and cinnamon in shallow dish. Stir in milk. 2. Dip bread in egg mixture, turning to coat both sides evenly. 3. Cook bread slices on lightly greased nonstick griddle or skillet on medium heat until browned on both sides. Serve with Easy Spiced Syrup, if desired. 4. Add 1 teaspoon McCormick Pure Vanilla Extract and 1/4 teaspoon Ground Cinnamon to 1 cup pancake syrup; stir well to mix. Serve warm, if desired.',
            url: 'https://i.ibb.co/pdLLBN7/joseph-gonzalez-zc-Ugjyq-Ewe8-unsplash.jpg" alt="joseph-gonzalez-zc-Ugjyq-Ewe8-unsplash'
          },
          {
            id: 2,
            title: 'Chicken Noodle Soup',
            instructions: '1. Pat chicken dry with paper towels; sprinkle with salt and pepper. In a 6-qt. stockpot, heat oil over medium-high heat. Add chicken in batches, skin side down; cook until dark golden brown, 3-4 minutes. Remove chicken from pan; remove and discard skin. Discard drippings, reserving 2 tablespoons. 2. Add onion to drippings; cook and stir over medium-high heat until tender, 4-5 minutes. Add garlic; cook 1 minute longer. Add broth, stirring to loosen browned bits from pan. Bring to a boil. Return chicken to pan. Add celery, carrots, bay leaves and thyme. Reduce heat; simmer, covered, until chicken is tender, 25-30 minutes. 3. Transfer chicken to a plate. Remove soup from heat. Add noodles; let stand, covered, until noodles are tender, 20-22 minutes. 4. Meanwhile, when chicken is cool enough to handle, remove meat from bones; discard bones. Shred meat into bite-sized pieces. Return meat to stockpot. Stir in parsley and lemon juice. If desired, adjust seasoning with additional salt and pepper. Discard bay leaves.',
            url: 'https://i.ibb.co/BzXMxgZ/Quick-Chicken-Noodle-Soup-22.jpg'
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
    padding:0px 30px;
  }
</style>