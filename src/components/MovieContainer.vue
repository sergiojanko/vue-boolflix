<template>
  <section id="movies">
    <div class="container">
        <h2>FILM</h2>
      <div class="row">
        <MovieCard
         v-for="(movie, index) in this.series" :key="index"
         :movie="movie"
         />
      </div>
       <h2>SERIE TV</h2>
      <div class="row">
        <MovieCard
         v-for="(movie, index) in this.movies" :key="index + movie"
         :movie="movie"
         />
      </div>
    </div>
  </section>
</template>

<script>
import MovieCard from "@/components/MovieCard.vue";

export default {
name: "MovieContainer",
components:{
    MovieCard,
},
props: ["movies", "series"],
created(){
  console.log(this.movie)
}

}


</script>

<style scoped>
#movies
{
padding-top: 80px;
background-color: gray;
min-height:100vh
}

.container .row
{
  display: flex;
  flex-wrap: wrap;
}
.container .row h2 
{
  width: 100%;
}


</style>