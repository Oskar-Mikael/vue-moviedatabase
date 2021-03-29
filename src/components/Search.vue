<template>
  <div>
    <form @submit="searchMovie">
      <input
        class="bg-gray-100 p-2 outline-none w-60"
        v-model="searchText"
        name="search"
        type="text"
        placeholder="Search Movie"
      />
      <br>
      <button class="mt-4 py-1 px-2 rounded bg-green-400 font-bold outline-none hover:bg-green-300 transition" type="submit">Search </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Search",

  data() {
    return {
      searchText: "",
    };
  },
  methods: {
    searchMovie(e) {
      e.preventDefault();
     
      this.$emit("search-movie", this.searchText);
      console.log(this.searchText)

      this.searchText = ''
    },
  },
};
</script>

<style>
</style>