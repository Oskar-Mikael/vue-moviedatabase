<template>
  <div id="app">
    <Header/>
    <HelloWorld />
    <MovieList />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import MovieList from "./components/MovieList.vue";
import Header from './layouts/Header.vue';

export default {
  name: "App",
  components: {
    HelloWorld,
    MovieList,
    Header,
  },

  methods: {},
};
</script>

<style>
  body {
    background: rgb(233, 233, 233);
  }
</style>
