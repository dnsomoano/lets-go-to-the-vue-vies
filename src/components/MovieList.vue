<template>
    <section>
      <!-- <form v-on:submit.prevent="addSearchTerm">
        <input type="text" placeholder="Movie title here" v-model="inputTerm" v-on:keyup.enter="addSearchTerm" />
        <button>Search</button>
      </form> -->
        <section class="movie-list">
            <MovieDetail v-for="movie in movies" :key="movie.id" :movieResult="movie" v-on:add-to-save="addToStorage" />
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
  mounted: function() {
    // this.getSearchResults();
  },
  methods: {
    addToStorage: function(title) {
      const bag = this.savedMovies.concat(title);
      localStorage.setItem("storedMovies", bag);
      this.savedMovies = bag;
      // TODO fix button disable
      // this.disableButton = true;
    }
    // addSearchTerm: function() {
    //   console.log(this.searchTerm);
    //   this.searchTerm = this.inputTerm;
    //   console.log(this.searchTerm);
    // },
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
