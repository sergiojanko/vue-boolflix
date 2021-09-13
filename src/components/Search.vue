<template>
  <div>
    <input type="text" name="search-term" id="search-bar" placeholder="Cerca un film o una serie tv" v-model="searchTerm" @keyup.enter="emitMovies">
    <button @click="emitMovies">Cerca</button>
  </div>
</template>

<script>



export default {
name: "Search",
data(){
    return {
        searchTerm: "",
    }
},
methods:{
  emitMovies(){
    this.$emit("movie", this.searchTerm);
      }
}
}

</script>

<style>

</style>