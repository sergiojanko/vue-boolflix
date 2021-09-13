<template>
  <div>
    <ul>
      <li>{{movie.title}}</li>
        <li>{{movie.original_title}}</li>
        <li v-if="movie.original_language == 'en'"><img src="../assets/images/en.png" alt="en" ></li>
        <li v-else><img src="../assets/images/it.png" alt="it"></li>
        <li>{{movie.vote_average}}</li>
        <li><img :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt=""></li>
      
    </ul>
  </div>
</template>

<script>
export default {
name: "MovieCard",
props: ["movie"],
methods: {
  // getPic(url){

  // }
}
// created(){
//   console.log(this.movie)
// }
}
</script>

<style>

</style>