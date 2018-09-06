<template>
<ul>
    <header>{{movieResult.title}}</header>
    <img :src="addImage(movieResult.poster_path)" alt="kats"/>
    <header>Release Date: {{movieResult.release_date}}</header>
    <p>{{movieResult.overview}}</p>
</ul>
</template>

<script>
export default {
  name: "MovieDetail",
  props: {
    movieResult: Object
  },
  data: function() {
    return {};
  },
  methods: {
    addImage: function(poster_path) {
      return "https://image.tmdb.org/t/p/w500/" + poster_path;
    }
  }
};
</script>

<style scoped>
</style>
