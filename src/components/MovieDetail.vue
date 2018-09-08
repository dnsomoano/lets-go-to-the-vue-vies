<template>
<section class="movie-box">
  <ul>
    <li>
    <header class="title-style">{{movieResult.title}}</header>
    <img class="poster" :src="addImage(movieResult.poster_path)" />
    <header class="release-date">Release Date: {{movieResult.release_date}}</header>
    <section class="box-synopsis">{{movieResult.overview}}</section>
    </li>
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
/* Imported fonts */
/* Title font */
@import url('https://fonts.googleapis.com/css?family=Six+Caps');
/* Body font */
@import url('https://fonts.googleapis.com/css?family=Archivo+Narrow');
/* @import url("https://fonts.googleapis.com/css?family=Caveat"); */

* {
  background-color: #2c3e50;
}

/* #CFDBD5 is for movie containers holding the title, poster, and overview */
/* #373636 is for banners, movie titles, release dates, and overviews */
.movie-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #CFDBD5;
  border: 0.2em double #373636;
  border-radius: 0.5em;
  text-align: center;
  margin: 0.5em;
  padding: 0em;
}

.movie-box ul {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #CFDBD5;
  margin: 0.3em;
  padding: 0em;
}

.movie-box li {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #CFDBD5;
  max-width: 18em;
}

.title-style {
  background-color: #CFDBD5;
  font-family: 'Six Caps', sans-serif;
  font-size: 2.2em;
  font-weight: bold;
  margin: 0em;
  margin-bottom: 0.3em;
}

.poster {
  border: 0.3em outset #373636;
  border-radius: 0.2em;
  height: 75%;
  width: 30%;
}

.release-date {
    background-color: #CFDBD5;
  font-family: 'Six Caps', sans-serif;
  font-size: 1.6em;
  margin: 0em;
  margin-bottom: 0.3em;
}

/* #AA8F66 is for overview container */
.box-synopsis {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #AA8F66;
  border: 1px outset #8a8a8a;
  border-radius: 0.3em;
  color: #373636;
  font-family: 'Archivo Narrow', sans-serif;
  font-size: 1em;
  margin: 0em;
  max-width: 17em;
  padding: 0.3em;
  text-align: center;
}

</style>
