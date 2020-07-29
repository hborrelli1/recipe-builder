<template>
  <section>
    <header>
      <h3>Recipes:</h3>
      <input 
        type="text" 
        placeholder="search for recipes..." 
        v-model="searchQuery"
        name="searchQuery"
        v-on:keyup="setSearchQuery"
      />
      <button
        v-on:click="resetSearchQuery"
      >Clear</button>
    </header>
    <div class='recipes-list'>
      <RecipeItem 
        v-for='recipe in data'
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
    props: ['recipes'],
    data() {
      return {
        data: this.recipes,
        searchQuery: ''
      }
    },
    methods: {
      setSearchQuery() {
        if (this.searchQuery) {
          let regex = RegExp((this.searchQuery), 'gi');
          this.data = this.recipes.filter(recipe => regex.test(recipe.title) || regex.test(recipe.instructions));
        } else {
          this.data = this.recipes;
        }
      },
      resetSearchQuery() {
        this.searchQuery = '';
        this.data = this.recipes;
      }
    }
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