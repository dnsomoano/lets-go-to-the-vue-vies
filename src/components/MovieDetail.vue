<template>
<section class="movie-box">
  <ul>
    <header>{{movieResult.title}}</header>
    <img class="poster" :src="addImage(movieResult.poster_path)" alt="kats"/>
    <header>Release Date: {{movieResult.release_date}}</header>
    <p class="box-synopsis">{{movieResult.overview}}</p>
  </ul>
</section>
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
.movie-box {
  display: flex;
  flex-direction: column;
  justify-content: center;
  border: 0.2em double black;
  text-align: center;
  margin: 0.5em;
}

.box-synopsis {
  max-width: 35em;
  text-align: center;
}

.poster {
  height: 75%;
  width: 50%;
}
</style>
