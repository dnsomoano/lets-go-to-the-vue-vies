<template>
  <div id="app">
    <header class="search-title">Search Movie By Title:</header>
    <!-- TODO make the search bar functional by storing the input and passing it down to MovieList child -->
    <form class="form-style" v-on:submit.prevent="getSearchResults">
      <input class="search-bar" type="text" placeholder="Movie title here..." v-on:focus="searchTerm = ''" v-model="searchTerm" />
      <button class="search-button" type="submit" name="search-button">Search</button>
    </form>
    <MovieList :movies="movies" />
    <footer id="dev-footer">®Created by Daniel N Somoano</footer>
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
      movies: []
    };
  },
  mounted: function() {
    this.getSearchResults();
  },
  methods: {
    testing: function() {
      // console.log("testing", this.searchTerm);
    },
    getSearchResults: function() {
      // console.log("getting", this.searchTerm);
      if (this.searchTerm) {
        let URL = `https://api.themoviedb.org/3/search/movie?api_key=e99344bac0d2a5336621a8492eeb2e74&language=en-US&query=${
          this.searchTerm
        }&page=1&include_adult=true`;
        // console.log(URL);
        fetch(URL)
          .then(resp => resp.json())
          .then(data => {
            console.log(data);
            this.movies = data.results;
          });
      } else {
        const TRENDING = `https://api.themoviedb.org/3/trending/all/day?api_key=e99344bac0d2a5336621a8492eeb2e74`;
        fetch(TRENDING)
          .then(resp => resp.json())
          .then(data => {
            console.log(data);
            this.movies = data.results;
          });
      }
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
  background-color: #373636;
}

* {
  background-color: #2c3e50;
}

.search-title {
  background-color: #373636;
  color: whitesmoke;
  font-size: 2em;
}

.form-style {
  background-color: #373636;
  margin-bottom: 1em;
}

.search-bar {
  background-color: white;
  border-radius: 0.2em;
}

.search-button {
  background-color: #2C3E50;
  border-radius: 0.2em;
  color: whitesmoke;
}

#dev-footer {
  background-color: #373636;
  color: whitesmoke;
  font-size: 1em;
}
</style>
