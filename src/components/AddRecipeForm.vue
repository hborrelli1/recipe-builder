<template>
  <div>
    <header>
      <h2>Create a New Recipe:</h2>
    </header>
    <form @submit="addRecipe">
      <input 
        type="text" 
        placeholder="Title of recipe..."
        v-model="title"
        name="title"
      />
      <textarea
        v-model="instructions"
        placeholder="instructions here..."
      ></textarea>
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>
  export default {
    name: 'AddRecipeForm',
    data() {
      return {
        title: '',
        instructions: ''
      }
    },
    methods: {
      addRecipe(e) {
        e.preventDefault();
        const newRecipe = {
          title: this.title,
          instructions: this.instructions
        }
        this.$emit('add-recipe', newRecipe)
        this.title = '';
        this.instructions = '';
      }
    }
  }
</script>

<style scoped>

</style>