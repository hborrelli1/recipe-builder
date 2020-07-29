<template>
  <section>
    <header>
      <h3>Recipes:</h3>
      <div class="search-bar">
        <input 
          type="text" 
          placeholder="Search for recipes..." 
          v-model="searchQuery"
          name="searchQuery"
          v-on:keyup="setSearchQuery"
        />
        <button
          v-on:click="resetSearchQuery"
        >Clear</button>
      </div>
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
          // this.$emit('set-query', regex)
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
    display: flex;
    justify-content: space-between;
    text-align:center;
    padding:10px 0px;
    border-bottom:1px solid #000;
    margin-bottom:20px;
  }

  .search-bar input,
  .search-bar button {
    height:40px;
    font-size:16px;
    padding:4px;
  }

  /* .search-bar button {
    height:40px;
    padding:0px 20px;
    border:0;
  } */

  .recipes-list {
    display: flex;
    flex-flow:wrap;
    justify-content: flex-start;
  }

</style>