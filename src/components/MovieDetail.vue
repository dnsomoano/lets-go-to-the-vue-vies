<template>
  <section class="movie-box">
    <ul>
      <li>
        <header class="title-style">{{movieResult.title || movieResult.name}}</header>
        <img class="poster" v-if="movieResult.poster_path" :src="addImage(movieResult.poster_path)" />
        <header class="release-date">
          <span class="subtext">Release Date:</span>
          {{movieResult.release_date || movieResult.first_air_date}}
        </header>
        <section class="box-synopsis">{{movieResult.overview}}</section>
        <button class="save-button" type="submit" @click="addToSave(movieResult)">Save for Later</button>
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
    return {
      moviePick: ""
    };
  },
  // mounted() {
  //   if (localStorage.storedMovies) {
  //     this.savedMovies = localStorage.storedMovies;
  //   }
  // },
  methods: {
    addImage: function(poster_path) {
      return "https://image.tmdb.org/t/p/w500/" + poster_path;
    },
    addToSave: function() {
      console.log("firing event", this.movieResult.title);
      this.$emit("add-to-save", this.movieResult.title);
    }
  }
};
</script>

<style scoped>
/* Imported fonts */
/* Title font */
@import url("https://fonts.googleapis.com/css?family=Six+Caps");
/* Body font */
@import url("https://fonts.googleapis.com/css?family=Archivo+Narrow");
/* @import url("https://fonts.googleapis.com/css?family=Caveat"); */

* {
  background-color: #dc493a;
}

/* #CFDBD5 is for movie containers holding the title, poster, and overview */
/* #373636 is for banners, movie titles, release dates, and overviews */
.movie-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #cfdbd5;
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
  background-color: #cfdbd5;
  margin: 0.3em;
  padding: 0em;
}

.movie-box li {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #cfdbd5;
  max-width: 18em;
}

.title-style {
  background-color: #cfdbd5;
  color: #373636;
  font-family: "Six Caps", sans-serif;
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
  background-color: #cfdbd5;
  font-family: "Six Caps", sans-serif;
  font-size: 1.6em;
  margin: 0em;
  margin-bottom: 0.3em;
}

.subtext {
  background-color: #cfdbd5;
  color: #373636;
  font-size: 1em;
  font-weight: 600;
}

/* #AA8F66 is for overview container */
.box-synopsis {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #aa8f66;
  border: 1px outset #8a8a8a;
  border-radius: 0.3em;
  color: #373636;
  font-family: "Archivo Narrow", sans-serif;
  font-size: 1em;
  margin: 0em;
  max-width: 17em;
  padding: 0.3em;
  text-align: center;
}

.save-button {
  display: flex;
  flex-direction: initial;
  background-color: #373636;
  border-radius: 0.3em;
  color: #e8eddf;
  margin-top: 0.3em;
  margin-bottom: 0em;
}
</style>
