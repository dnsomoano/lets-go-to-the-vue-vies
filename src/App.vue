<template>
  <div id="app">
    <header>Search for a movie:</header>
    <!-- TODO make the search bar functional by storing the input and passing it down to MovieList child -->
    <!-- <form v-on:submit.prevent="addSearchTerm">
      <input type="text" placeholder="Movie title here" v-model="searchTerm" />
      <button type="button" name="search-button" v-on:click="addSearchTerm">Search</button>
    </form> -->
    <MovieList />
  </div>
</template>

<script>
import MovieList from "./components/MovieList.vue";

export default {
  name: "app",
  components: {
    MovieList
  }
  // data: function() {
  //   searchTerm: "";
  // }
  // methods: {
  //   addSearchTerm: function() {
  //     console.log("Button clicked");
  //     this.searchTerm += "";
  //     console.log(this.searchTerm);
  //   }
  // }
};
</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
