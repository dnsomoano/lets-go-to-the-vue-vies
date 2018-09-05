<template>
<ul>
    <header>{{movie.title}}</header>
    <img src="https://placekitten.com/408/287" alt="kats"/>
    <header>Release Date: {{movie.release_date}}</header>
    <p>{{movie.overview}}</p>
</ul>
</template>

<script>
export default {
  name: "SearchMovie",
  props: {
      movieResultsFromSearch
  },
  data: function() {
    return {
      movies: [{}]
    };
  }
};
</script>

<style>
</style>
