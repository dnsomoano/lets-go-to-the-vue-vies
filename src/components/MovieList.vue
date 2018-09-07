<template>
    <section>
      <!-- <form v-on:submit.prevent="addSearchTerm">
        <input type="text" placeholder="Movie title here" v-model="inputTerm" v-on:keyup.enter="addSearchTerm" />
        <button>Search</button>
      </form> -->
        <section class="movie-list">
            <MovieDetail v-for="movie in movies" :key="movie.id" :movieResult="movie" />
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
    searchQuery: String,
    movies: Array
  },
  // data: function() {
  //   return {
  //     // searchTerm: "",
  //     // inputTerm: "",
  //     movies: []
  //   };
  // },
  methods: {
    // addSearchTerm: function() {
    //   console.log(this.searchTerm);
    //   this.searchTerm = this.inputTerm;
    //   console.log(this.searchTerm);
    // },
   
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
  font-size: 1.5em;
  text-align: center;
}

* {
  background-color: #2c3e50;
}
</style>
