<template>
  <div id="app">
      <header>
        <div class="logo"></div>
        <Search @movie="getMovies" />
        <span @movie=movie></span>
      </header>
      <MovieContainer :movies="movies" :series="series"/>
  </div>
</template>

<script>
import axios from "axios";
import Search from './components/Search.vue'
import MovieContainer from './components/MovieContainer.vue'

export default {
  name: 'App',
  components: {
    Search,
    MovieContainer,
  },
  data(){
    return {
      baseUri: "https://api.themoviedb.org/3",
      apiKey: "e07987eab392b20b26978bcf1d6dcd5d",
      movies: [],
      series: [],
      movie: "",
    }
  },
  methods: {
    getMovies(movie){
      if (!movie) this.movies= [];
      this.movie = movie;
      this.getData("movies");
      this.getData("tv");

        console.log(this.series);
        console.log(this.movies);

  },

  getData(entity){
    if (entity == "movies") {
      axios.get(`${this.baseUri}/search/movie/?api_key=${this.apiKey}&query=${this.movie}`)
      .then((res) => {
      this.movies = res.data.results;
      })
    }
    else if (entity == "tv" ) {
      axios.get(`${this.baseUri}/search/tv/?api_key=${this.apiKey}&query=${this.movie}`)
      .then((res) => {
      this.series = res.data.results;
      })
  }
  }
}
}
</script>

<style lang="scss">

*
{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

header
{
  height: 80px;
  width: 100%;
  position: fixed;
  left: 0;
  top: 0;
  background-color: black;
}
</style>
