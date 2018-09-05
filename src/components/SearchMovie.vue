<template>
    <section>
        <header>Search for a movie:</header>
        <input type="text" placeholder="Movie title here"/>
        <header>{{movies[0].title}}</header>
        <img src="https://placekitten.com/408/287" alt="kats"/>
        <header>Release date</header>
        <p>Movie overview</p>
        </section>
</template>

<script>
export default {
  name: "SearchMovie",
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
          console.log(data)
          this.movies = data.results;
      });
        // console.log(this.movies);
  }
};
</script>

<style scoped>
</style>
