<template>
  <div id="app">
    <header class="text-center mt-16">
      <h1 class="text-4xl font-bold">Vue Movie Database</h1>
      <p>By Oskar Boström</p>
    </header>
    <HelloWorld />
    <MovieList />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import MovieList from "./components/MovieList.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    MovieList,
  },

  methods: {},
};
</script>

<style>
  body {
    background: rgb(233, 233, 233);
  }
</style>
