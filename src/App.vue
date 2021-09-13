<template>
  <div id="app">
      <header>
        <div class="logo"></div>
        <Search @movie="getMovies" />
        <span @movie=movie></span>
      </header>
      <MovieCard/>
  </div>
</template>

<script>
import axios from "axios";
import Search from './components/Search.vue'
import MovieCard from './components/MovieCard.vue'

export default {
  name: 'App',
  components: {
    Search,
    MovieCard
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

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
