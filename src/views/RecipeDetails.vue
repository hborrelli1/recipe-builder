<template>
  <article>
    <img :src="getImgSrc()" :alt="recipe.title" />
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
    methods: {
      getImgSrc() {
        let imageUrl = this.recipe.url ? this.recipe.url : require('../assets/' + 'default-placeholder-img.jpg');
        return imageUrl;
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