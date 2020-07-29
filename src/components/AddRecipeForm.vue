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
      <input 
        type="text" 
        placeholder="Image url..."
        v-model="url"
        name="url"
      />
      <textarea
        v-model="instructions"
        placeholder="instructions here..."
      ></textarea>
      <button :disabled="!formIsValid" class="btn">Submit</button>
    </form>
  </div>
</template>

<script>


  export default {
    name: 'AddRecipeForm',
    data() {
      return {
        title: '',
        url: '',
        instructions: ''
      }
    },
    computed: {
      titleIsValid() {
        return !!this.title;
      },
      instructionsAreValid() {
        return !!this.instructions;
      },
      formIsValid() {
        return this.titleIsValid && this.instructionsAreValid;
      }
    },
    methods: {
      addRecipe(e) {
        e.preventDefault();

        if (this.formIsValid) {
          console.log('submitting form');
          const newRecipe = {
            title: this.title,
            instructions: this.instructions,
            id: Date.now(),
            url: this.url
          }
          this.$emit('add-recipe', newRecipe)
          this.title = '';
          this.url = '';
          this.instructions = '';
        } else {
          console.log('form not valid');
        }
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
  textarea,
  button {
    margin-bottom:5px;
    height: 30px;
    padding:3px;
  }

  textarea {
    height:50px;
  }

  button {
    background-color:#333;
    color:#f4f4f4;
    font-weight:600;
    font-size:16px;
    border:0;
    transition: all .3s;
  }

  button:hover {
    cursor:pointer;
    opacity: .8;
    transition: all .3s;
  }

  button:disabled {
    opacity:.4;
    cursor:no-drop;
  }
</style>