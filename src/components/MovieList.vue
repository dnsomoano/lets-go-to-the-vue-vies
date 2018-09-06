<template>
    <section>
        <ul>
            <MovieDetail v-for="movie in movies" :key="movie.id" :movieResult="movie" />
        </ul>
        </section>
</template>

<script>
import MovieDetail from "./MovieDetail.vue";

export default {
  name: "MovieList",
  components: {
    MovieDetail
  },
  data: function() {
    return {
      movies: []
    };
  },
  // TODO pass searchTerm as a prop to query on line 24
  mounted: function() {
    const URL = `https://api.themoviedb.org/3/search/movie?api_key=e99344bac0d2a5336621a8492eeb2e74&language=en-US&query=meg&page=1&include_adult=false`;

    fetch(URL)
      .then(resp => resp.json())
      .then(data => {
        console.log(data);
        this.movies = data.results;
      });
  }
};
</script>

<style scoped>
</style>
