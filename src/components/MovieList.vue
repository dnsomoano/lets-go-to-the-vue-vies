<template>
    <section>
      <form v-on:submit.prevent="addSearchTerm">
        <input type="text" placeholder="Movie title here" v-model="inputTerm" v-on:keyup.enter="addSearchTerm" />
        <button>Search</button>
      </form>
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
  // props: {
  //   searchQuery: String
  // },
  data: function() {
    return {
      searchTerm: "",
      inputTerm: "",
      movies: []
    };
  },
  methods: {
    addSearchTerm: function() {
      console.log(this.searchTerm);
      this.searchTerm = this.inputTerm;
      console.log(this.searchTerm);
    },
    getSearchResults: function() {
      if (this.searchTerm) {
        let URL = `https://api.themoviedb.org/3/search/movie?api_key=e99344bac0d2a5336621a8492eeb2e74&language=en-US&query=${
          this.searchTerm
        }&page=1&include_adult=false`;
        console.log(URL);
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
  },
  // TODO pass searchTerm as a prop to query on line 24
  mounted: function() {
    this.getSearchResults();
  },
  // computed: function() {
  //   this.getSearchResults();
  // }
};
</script>

<style scoped>
.movie-list {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;
  margin: 0.5em;
}
</style>
