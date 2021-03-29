<template>
  <div>
    <div class="my-10">
      <img
        class="w-80 mx-auto"
        v-if="movie.Poster == 'N/A'"
        src="../assets/no-image.png"
        alt="No image"
      />
      <img class="mx-auto h-96" v-else :src="movie.Poster" />
      <h2 class="text-bold text-2xl mt-4">{{ movie.Title }}</h2>
      <h3>{{ movie.Year }}</h3>
      <button
        class="mt-4 py-1 px-2 rounded bg-blue-400 font-bold outline-none hover:bg-blue-300 transition"
        v-on:click="getMovie"
      >
        More info
      </button>
    </div>
    <div v-if="this.movieInfo.length == 0"></div>

    <div v-else>
      <MovieInfo>
          <img src="../assets/close.png"
          class="cursor-pointer float-right font-bold focus:outline-none "
          v-on:click="closeMovie"
        />

        <h2 class="font-bold text-3xl mb-4">{{ movieInfo.Title }}</h2>

        <img class="mx-auto w-2/5 sm:w-1/2 border-2 border-white" :src="movieInfo.Poster"/>

        <h3 class="font-bold">Genres:</h3>
        <p>{{ movieInfo.Genre }}</p>

        <h3 class="font-bold">Director:</h3>
        <p>{{ movieInfo.Director }}</p>

        <h3 class="font-bold">Actors:</h3>
        <p>{{ movieInfo.Actors }}</p>

        <h3 class="font-bold">Release Date:</h3>
        <p>{{ movieInfo.Released }}</p>

        <h3 class="font-bold">Country:</h3>
        <p>{{ movieInfo.Country }}</p>

        <h3 class="font-bold">Runtime:</h3>
        <p>{{ movieInfo.Runtime }}</p>

        <h3 class="font-bold">IMDB Rating:</h3>
        <p>{{ movieInfo.imdbRating }}</p>
      </MovieInfo>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import MovieInfo from "./MovieInfo";
export default {
  name: "Movie",
  props: ["movie"],

  components: {
    MovieInfo,
  },
  data() {
    return {
      movieInfo: [],
      apiKey: process.env.VUE_APP_API_KEY
    };
  },

  methods: {
    getMovie() {
      this.movieId = this.movie.imdbID
      axios
        .get("https://www.omdbapi.com/?i=" + this.movieId + "&apikey=" + this.apiKey)
        .then((response) => {
          this.movieInfo = response.data;
          console.log(response.data);
        });
    },

    closeMovie() {
      this.movieInfo = [];
    },
  },
};
</script>

<style scoped>
</style>