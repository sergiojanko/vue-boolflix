<template>
  <div>
    <ul>
      <li>
        {{movie.title}}
        {{movie.original_title}}
        {{movie.original_language}}
        {{movie.vote_average}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
name: "MovieCard",
props: ["movie"],
// created(){
//   console.log(this.movie)
// }
}
</script>

<style>

</style>