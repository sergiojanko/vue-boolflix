<template>
  <div>
    <ul>
      <li>{{movie.title}}</li>
        <li>{{movie.original_title}}</li>
        <li v-if="movie.original_language == 'en'"><img src="../assets/images/en.png" alt="en" ></li>
        <li v-else><img src="../assets/images/it.png" alt="it"></li>
        <li><i v-for="n in getVote(movie.vote_average)" :key="n" class="fas fa-star"></i></li>
        <li><img :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt=""></li>
      
    </ul>
  </div>
</template>

<script>
export default {
name: "MovieCard",
props: ["movie"],
methods: {
getVote(vote){
  return Math.ceil(vote/2)
}
}
// created(){
//   console.log(this.movie)
// }
}
</script>

<style>

</style>