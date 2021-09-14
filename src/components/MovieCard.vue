<template>
  <div>
    <ul class="card">
        <li class="pic"><img :src="imgPath" alt=""></li>
        <li class="info">Titolo: {{movie.title || movie.name}}</li>
        <li class="info">Titolo originale: {{movie.original_title}}</li>
        <li class="info" v-if="movie.original_language == 'en'"><img class="lang" src="../assets/images/en.png" alt="en" ></li>
        <li class="info" v-else><img class="lang" src="../assets/images/it.png" alt="it"></li>
        <li class="info">Voto: <i v-for="n in 5" :key="n" class="fa-star" :class="(n < vote) ? 'fas' : 'far'"></i></li>
        <li class="info">Trama: {{movie.overview}}</li>
      
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
  imgPath(){
    if (this.movie.poster_path) return `https://image.tmdb.org/t/p/w342/${this.movie.poster_path}`;
    return `https://www.altavod.com/assets/images/poster-placeholder.png`
  }
}
// created(){
//   console.log(this.movie)
// }
}
</script>

<style scoped>
li
{
  list-style-type: none;
}

div
{
  width: 342px;
  border: white;
  margin: 20px 30px;
}

.card .info
{
  display: none;
}
.pic img
{
  max-width: 342px;
  object-fit: contain;

}
.card:hover .pic
{
display: none;
}
.card:hover .info
{
display: block;
}

.lang
{
  max-width: 30px;
}


</style>