<template>
  <div id="app">
    <header class="title">
      <!-- <img alt="MovieDB logo" src="./assets/the-movie-db-logo.svg"> -->
      The Movie DB
    </header>
    <section class="search-container">
      <header>Search by Title:</header>
      <form class="form-style" v-on:submit.prevent="getSearchResults(selection)">
        <input class="search-bar" type="text" placeholder="Movie title here..." v-on:focus="searchTerm = ''" v-model="searchTerm" />
        <select v-model="selection">
          <option value=""> --Choose media-- </option>
          <option value="movies">Movies</option>
          <option value="tv shows" selected>TV Shows</option>
        </select>
        <button class="search-button" type="submit" name="search-button">Search</button>
        </form>
        <section>
        <button class="cart-button">{{this.cart.length}}</button>
        </section>
    </section>
    <MovieList :movies="movies" />
    <a href="https://github.com/dnsomoano">
    <footer id="dev-footer">® Created by Daniel N Somoano</footer>
    </a>
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
    let fromStorage = localStorage.getItem("storedMovies");
    fromStorage = fromStorage ? fromStorage.split(",") : [];
    return {
      cart: fromStorage,
      searchTerm: "",
      selection: "",
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
    getSearchResults: function(selection) {
      // console.log("getting", this.searchTerm);
      if ((selection = "tv shows")) {
        if (this.searchTerm) {
          let TV_URL = `https://api.themoviedb.org/3/search/tv?api_key=e99344bac0d2a5336621a8492eeb2e74&language=en-US&query=${
            this.searchTerm
          }&page=1&include_adult=true`;
          // console.log(TV_URL);
          fetch(TV_URL)
            .then(resp => resp.json())
            .then(data => {
              console.log(data);
              this.movies = data.results;
            });
        }
      } else if ((selection = "movies")) {
        if (this.searchTerm) {
          let MOVIES_URL = `https://api.themoviedb.org/3/search/movies?api_key=e99344bac0d2a5336621a8492eeb2e74&language=en-US&query=${
            this.searchTerm
          }&page=1`;
          // console.log(MOVIES_URL);
          fetch(MOVIES_URL)
            .then(resp => resp.json())
            .then(data => {
              // console.log(data);
              this.movies = data.results;
            });
        }
      } else {
        const TRENDING = `https://api.themoviedb.org/3/trending/all/day?api_key=e99344bac0d2a5336621a8492eeb2e74`;
        fetch(TRENDING)
          .then(resp => resp.json())
          .then(data => {
            // console.log(data);
            this.movies = data.results;
          });
      }
    }
  }
};
</script>

<style scoped>
/* #dc493a is for background of page */
/* #373636 is for banners, movie titles, release dates, overviews, and footer */
/* #e8eddf is for titles, search bar & button */
/* #CFDBD5 is for movie containers holding the title, poster, and overview */
/* #AA8F66 is for overview container */
/* Imported fonts */
/* Title font */
@import url("https://fonts.googleapis.com/css?family=Six+Caps");
/* Body font */
@import url("https://fonts.googleapis.com/css?family=Archivo+Narrow");
/* @import url("https://fonts.googleapis.com/css?family=Caveat"); */

#app {
  /* font-family: "Avenir", Helvetica, Arial, sans-serif; */
  /* font-family: "Caveat", cursive; */
  font-family: "Archivo Narrow", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #373636;
}

* {
  background-color: #dc493a;
}

.title {
  background-color: #373636;
  color: #e8eddf;
  font-family: "Six Caps", sans-serif;
  font-size: 3.5em;
}

.search-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  color: #e8eddf;
  margin-top: 1.2em;
  padding: 0.5em;
}

.search-container header {
  color: #e8eddf;
  margin-right: 0.3em;
}

.form-style {
  /* background-color: #373636; */
  margin-bottom: 1em;
}

.search-bar {
  background-color: #cfdbd5;
  border-radius: 0.2em;
}

.search-button {
  background-color: #373636;
  border-radius: 0.2em;
  color: #e8eddf;
}

.cart-button {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  margin: 0.3em 1em 1em 1em;
}

#dev-footer {
  display: flex;
  flex-direction: row-reverse;
  justify-content: flex-start;
  background-color: #373636;
  color: #e8eddf;
  font-size: 0.8em;
  margin-right: 0.4em;
}
</style>
