<template>
  <article>
    <img :src="recipe.url" :alt="recipe.title" />
    <h1>{{ recipe.title }}</h1>
    <p>{{ recipe.instructions }}</p>
  </article>
</template>

<script>
  export default {
    name: 'RecipeDetails',
    props: ['recipe'],
    data() {
      return {
        id: this.$route.params.id,
        title: this.$route.params.title
      }
    },
    computed: {
      // recipe() {
      //   // return store.recipes.find(recipe => recipe.slug === this.slug)
      // }
    }
  }
</script>

<style scoped>

</style>