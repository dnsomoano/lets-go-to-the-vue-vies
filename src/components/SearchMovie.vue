<template>
    <section>
        <header>Search for a movie:</header>
        <input type="text" placeholder="Movie title here"/>
        <ul>
            <MovieResults v-for="movie in movies" v-bind:key="movie.id" v-bind:movieResultsFromSearch="movie" />
        </ul>
        </section>
</template>

<script>
export default {
  name: "SearchMovie",
  components: {
      MovieResults
  },
  data: function() {
    return {
      movies: [{}]
    };
  },
  mounted: function() {
    const URL = `https://api.themoviedb.org/3/search/movie?api_key=e99344bac0d2a5336621a8492eeb2e74&language=en-US&query=meg&page=1&include_adult=false`;

    fetch(URL)
      .then(resp => resp.json())
      .then(data => {
        console.log(data);
        this.movies = data.results;
      });
    // console.log(this.movies);
  }
};
</script>

<style scoped>
</style>
