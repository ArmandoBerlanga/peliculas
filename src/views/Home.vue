<template>

  <div class="home">

    <FeatureCard/>
    <SearchBox @search="passMovies"/>
    <MovieList :movies="moviesFound" :contentName="searched"/>
    
  </div>

</template>

<script>

  import { ref } from 'vue'
  import FeatureCard  from "../components/FeatureCard.vue"
  import SearchBox  from "../components/SearchBox.vue"
  import MovieList  from "../components/MovieList.vue"

  export default {
    components: { FeatureCard, SearchBox, MovieList },
    name: "Home",

    setup(){
      var moviesFound = ref([]);
      var searched = ref('');

      function passMovies (movies, search)
        {
            moviesFound.value = movies;
            searched.value = search;
        }

      return {
        moviesFound,
        searched,
        passMovies,
      }
    }
  }

</script>

<style scoped>

  .home{
    margin: 10px 5%;
  }

</style>
