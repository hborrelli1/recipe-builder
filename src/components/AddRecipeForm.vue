<template>
  <div class="recipes-form-container">
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
  .recipes-form-container {
    display: flex;
    flex-flow:column;
  }

  header {
    text-align:center;
    padding:20px 0px;
  }

  form {
    width:100%;
    max-width:400px;
    display: flex;
    flex-flow:column;
    margin:0 auto 50px;
  }

  input, 
  textarea {
    margin-bottom:5px;
    height: 30px;
    padding:3px;
  }

  textarea {
    height:50px;
  }

  input[type='submit'] {
    background-color:#333;
    color:#f4f4f4;
    font-weight:600;
    font-size:16px;
    border:0;
  }
</style>