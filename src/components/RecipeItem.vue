<template>
  <div class="recipe-item">
    <button
      @click="$emit('del-recipe', recipe.id)"
    >X</button>
    <router-link 
      :to='{name: "RecipeDetails", params: {recipe: recipe, id: recipe.id}}'
      class="recipe-link"
    >
      <img :src="getImgSrc()" :alt="recipe.title" />
      <h4>{{ recipe.title }}</h4>
      <!-- <p>{{ recipe.instructions }}</p> -->
    </router-link>
  </div>
</template>

<script>
  export default {
    name: 'RecipeItem',
    props: ['recipe'],
    methods: {
      getImgSrc() {
        let imageUrl = this.recipe.url ? this.recipe.url : require('../assets/' + 'default-placeholder-img.jpg');
        return imageUrl;
      }
    }
  }
</script>

<style scoped>
  .recipe-item {
    width:32%;
    padding:20px;
    background-color:#f4f4f4;
    margin-right:2%;
    margin-bottom:20px;
    position:relative;
  }
  
  .recipe-item:nth-of-type(3n) {
    margin-right:0px;
  }

  .recipe-link {
    text-decoration:none;
    color:#333;
  }

  button {
    position:absolute;
    top:10px;
    right:10px;
    border:0;
  }

  button:hover {
    cursor:pointer;
  }
</style>