<template>
    <section>
      <!-- <form v-on:submit.prevent="addSearchTerm">
        <input type="text" placeholder="Movie title here" v-model="inputTerm" v-on:keyup.enter="addSearchTerm" />
        <button>Search</button>
      </form> -->
        <section class="movie-list">
            <MovieDetail v-for="movie in movies" :key="movie.id" :movieResult="movie" :addToLocalStorage="addMovieToStorage" />
        </section>
    </section>
</template>

<script>
import MovieDetail from "./MovieDetail.vue";

export default {
  name: "MovieList",
  components: {
    MovieDetail
  },
  props: {
    movies: Array
  },
  data: function() {
    return {
      savedMovies: []
      // disableButton: false
      // //     // searchTerm: "",
      // //     // inputTerm: "",
      // //     movies: []
    };
  },
  methods: {
    // addSearchTerm: function() {
    //   console.log(this.searchTerm);
    //   this.searchTerm = this.inputTerm;
    //   console.log(this.searchTerm);
    // },
    addMovieToStorage(movieTitle) {
      console.log(typeof movieTitle);
      const pick = this.savedMovies.concat(movieTitle);
      localStorage.setItem("storedMovies", pick);
      // console.log(typeof localStorage.saved - Movies);
      // TODO save more than one movie to local storage
      // TODO fix button disable
      this.savedMovies = pick;
      // dbg
      console.log("Saved movies are:", this.savedMovies);
      console.log(localStorage.storedMovies);
      this.disableButton = true;
    }
  },
  mounted: function() {
    // this.getSearchResults();
  }
};
</script>

<style scoped>
.movie-list {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  text-align: center;
}

/* #dc493a is for background of page */
* {
  background-color: #dc493a;
}
</style>
