<template>
  <div class="recipe-item">
    <router-link 
      :to='{name: "RecipeDetails", params: {recipe: recipe, id: recipe.id}}'
      class="recipe-link"
    >
      <img :src="getImgSrc()" :alt="recipe.title" />
      <h4>{{ recipe.title }}</h4>
    </router-link>
    <button
      @click="$emit('del-recipe', recipe.id)"
    >Remove Recipe</button>
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

  img {
    width: 100%;
    object-fit: cover;
    height: 250px;
  }

  h4 {
    margin-bottom:10px;
  }

  button {
    border:0;
  }

  button:hover {
    cursor:pointer;
    text-decoration:underline;
  }
</style>