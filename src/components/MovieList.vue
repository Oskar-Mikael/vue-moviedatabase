<template>
  <div class="text-center mt-20">
    <Search v-on:search-movie="getMovies" />
    <div class="mt-10" v-if="errorMessage">
      {{ errorMessage }}
    </div>
    <div class="grid gap-x-8 lg:grid-cols-3 sm:grid-cols-1">
      <div v-for="movie in movies" :key="movie.id">
        <Movie v-bind:movie="movie" />
      </div>

    </div>
    
  </div>
</template>

<script>
import axios from "axios";
import Movie from "./Movie";
import Search from "./Search.vue";
export default {
  name: "MovieList",

  components: {
    Search,
    Movie,
  },

  data() {
    return {
      movieSearchText: "",
      errorMessage: null,
      movies: [],
      apiKey: process.env.VUE_APP_API_KEY,
    };
  },

  methods: {
    getMovies(searchText) {
      this.movieSearchText = searchText;
      axios
        .get("https://www.omdbapi.com/?s=" + searchText + "&apikey=" + this.apiKey)
        .then((response) => {
          if (response.data.Response === "False") {
            this.errorMessage = "No movies were found";
          } else {
            console.log(response.data.Search);
            this.movies = response.data.Search;
            this.errorMessage = "";
          }
        });

        
    },
  },
};
</script>

<style scoped>

</style>