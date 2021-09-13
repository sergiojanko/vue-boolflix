<template>
  <div class="container">
    <MovieCard
     v-for="(movie, index) in this.movies" :key="index"
     :movie="movie"
     />
  </div>
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

<style>

</style>