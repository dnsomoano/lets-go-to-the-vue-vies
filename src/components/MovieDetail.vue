<template>
<section class="movie-box">
  <ul>
    <header class="title-style">{{movieResult.title}}</header>
    <img class="poster" :src="addImage(movieResult.poster_path)" />
    <header class="title-style">Release Date: {{movieResult.release_date}}</header>
    <section class="box-synopsis">{{movieResult.overview}}</section>
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
* {
  background-color: #2c3e50;
}

.movie-box {
  display: flex;
  flex-direction: column;
  justify-content: center;
  background-color: whitesmoke;
  border: 0.2em double black;
  border-radius: 0.5em;
  text-align: center;
  margin: 0.5em;
  padding: 0;
}

.movie-box ul {
  background-color: whitesmoke;
}

.title-style {
  background-color: whitesmoke;
  font-weight: bold;
  margin-bottom: 0.3em;
}

.box-synopsis {
  background-color: #BAB9B9;
  border: 1px outset #8A8A8A;
  border-radius: 0.2em;
  color: black;
  margin-left: 2.5em;
  max-width: 16em;
  padding: 0.3em;
  text-align: center;
}

.poster {
  border: 0.3em outset #131313;
  border-radius: 0.2em;
  height: 75%;
  width: 50%;
}
</style>
