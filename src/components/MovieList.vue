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
  methods: {
    // addSearchTerm: function() {
    //   console.log(this.searchTerm);
    //   this.searchTerm = this.inputTerm;
    //   console.log(this.searchTerm);
    // },
  },
  mounted: function() {
    // this.getSearchResults();
  },
  methods: {
    addToStorage: function(title) {
      console.log("catching event");
      console.log(typeof title);
      // savedMovies.push(title).split(",");
      // console.log(savedMovies);
      localStorage.setItem("storedMovies", title);
      // TODO save more than one movie to local storage
      // TODO fix button disable
      // this.disableButton = true;
    }
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
