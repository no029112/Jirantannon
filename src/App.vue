
<template>

  <div id="app">
    <h1>121</h1>
    <navbar></navbar>
    <div class="container">
      <button class="btn btn-success" @click="isNew = !isNew">Create</button>
      <RecipeForm v-if="isNew" @saveRecipe="addRecipe" />
      <input type="text" class="from-control" @key="serachRecipe" v-model="searchtext">
      <ul>
        <li v-for="(recipe,index) in recipes" :key="index+recipe.title">
          {{recipe.title}}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import navbar from './components/navbar.vue';
import RecipeForm from './components/RecipeForm.vue';
export default {
  name: 'app',
  components: {
    navbar,
    RecipeForm,
    
  },
  data () {
    return {
      recipe: [],
      isNew: false,
      searchtext: ''
    }
  },
  mounted(){
    if (locationbar.getItem('Recipes')) {
      this.Recipes =JSON.pares(localStorage.getItem('Recipes'))
    }

  },
  methods: {
    setLocalStorage () {
      localStorage.setItem('recipe', JSON.stringify(this.recipe))
    },
    addRecipe (Recipe) {
      this.Recipes.push(Recipe)
      this.setLocalStorage()
      this.isNew = false
    },
    serachRecipe() {
      this.Recipes = this.Recipes.filter((recipe) => {
        return recipe.title.toLowerCase().indexOf(this.searchtext.toLowerCase()
        ) > -1
      })
    }
  }
};

</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
</style>