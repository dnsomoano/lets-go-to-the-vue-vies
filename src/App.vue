<template>
  <div id="app">
    <header>Search for a movie:</header>
    <!-- TODO make the search bar functional by storing the input and passing it down to MovieList child -->
    <form v-on:submit.prevent="addSearchTerm">
      <input type="text" placeholder="Movie title here" v-model="inputTerm" />
      <button type="button" name="search-button">Search</button>
    </form>
    <MovieList :searchQuery="searchTerm" />
  </div>
</template>

<script>
import MovieList from "./components/MovieList.vue";

export default {
  name: "app",
  components: {
    MovieList
  },
  data: function() {
    return {
      searchTerm: "",
      inputTerm: ""
    };
  },
  methods: {
    addSearchTerm: function() {
      console.log("Button clicked");
      this.searchTerm = this.inputTerm;
      console.log("The search term is", this.searchTerm);
      console.log("The inputTerm term is", this.inputTerm);
    }
  }
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Caveat");
#app {
  /* font-family: "Avenir", Helvetica, Arial, sans-serif; */
  font-family: "Caveat", cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
