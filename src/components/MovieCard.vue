<template>
  <div>
    <ul>
      <li>{{movie.title}}</li>
        <li>{{movie.original_title}}</li>
        <li v-if="movie.original_language == 'en'"><img src="../assets/images/en.png" alt="en" ></li>
        <li v-else><img src="../assets/images/it.png" alt="it"></li>
        <li><i v-for="n in 5" :key="n" class="fa-star" :class="(n < vote) ? 'fas' : 'far'"></i></li>
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
},
computed: {
  vote(){return Math.ceil(this.movie.vote_average / 2)},
}
// created(){
//   console.log(this.movie)
// }
}
</script>

<style>

</style>