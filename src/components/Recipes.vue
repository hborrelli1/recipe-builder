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
        // let regex = `/${this.searchQuery}/gi`;
        // this.data = this.data.find(recipe => recipe.title.matches(regex) || recipe.instructions.matches(regex));
        if (this.searchQuery) {
          let regex = RegExp((this.searchQuery), 'gi');

          console.log('search query is valid');
          this.data = this.recipes.filter(recipe => regex.test(recipe.title) || regex.test(recipe.instructions));
          console.log(this.data);
          // return this.data.find(recipe => console.log(recipe));
        } else {
          console.log('normal recipes list');
          this.data = this.recipes;
        }
      }
    },
    computed: {
      recipesToDisplay() {
        // if searchQuery is not empty, 
        //    find all recipes that match any term.
        // If not, use all recipes

        // let regex = `/${this.searchQuery}/gi`;
        // this.data = this.data.find(recipe => recipe.title.matches(regex) || recipe.instructions.matches(regex));

        if (this.searchQuery) {
          let regex = RegExp(`/${this.searchQuery}/gi`);
          console.log('search query is valid');
          return this.data.filter(recipe => regex.test(recipe.title) || regex.test(recipe.instructions));
          // return this.data.find(recipe => console.log(recipe));
        } else {
          console.log('normal recipes list');
          return this.recipes;
        }
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