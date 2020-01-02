<template>
  <div id="app">
    <nav class="flex items-center justify-between flex-wrap shadow-md p-6">
      <div class="flex items-center flex-shrink-0 text-white mr-6">
        <span class="font-semibold text-xl tracking-tight">
          <img src="@/assets/logo.svg" alt="">
        </span>
      </div>
      <form class="" @submit.prevent="getResults">
        <input v-model="searchTerm" class="transition focus:outline-0 border border-transparent focus:bg-white
      focus:border-gray-300 placeholder-gray-600 rounded-lg bg-gray-200 py-2 pr-4 pl-10 block w-full
      appearance-none leading-normal" type="text" placeholder="Search">
      </form>
      <div class="block flex-grow">
        <a href="https://github.com/AssemblyWeb/vue-api" target="_blank"
          class="float-right hover:text-white">
          <img class="w-10" src="@/assets/github-brands.svg"
            alt="https://github.com/AssemblyWeb/vue-api">
        </a>
      </div>
    </nav>
    <!-- testgrid -->
    <!-- <div class=""> -->
      <div class="flex flex-grow mt-5">
        <div class="w-3/4 bg-gray-300 w-full">
            first
            <div class="flex flex-wrap">
              <movie v-for="movie in results" :key="movie.id" class="" :movie="movie"
                :addFav="addFav" :removeFav="removeFav">
              </movie>
            </div>
        </div>
        <div class="w-1/4 bg-gray-500">
         second
         <div v-for="movie in favs" :key="movie.id" class="flex">
            {{movie.Title}} {{movie.Year}}
            <a @click="removeFav(movie)" class="btn btn-primary">remove</a>
          </div>
        </div>
      </div>
    <!-- </div> -->
    <!-- test grid -->
    <!-- <div class="flex">
      <div class="">
        <div class="w-3/4">
          <div v-if="error" class="mt-3 alert alert-dismissible alert-danger">
            <strong>{{error}}</strong>
          </div>
          <div class="flex">
            <movie v-for="movie in results" :key="movie.id" class="w-1/3" :movie="movie"
              :addFav="addFav" :removeFav="removeFav">
            </movie>
          </div>
        </div>
        <div class="w-1/4">
          <div v-for="movie in favs" :key="movie.id">
            {{movie.Title}} {{movie.Year}}
            <a @click="removeFav(movie)" class="btn btn-primary">remove</a>
          </div>
        </div>
      </div>
    </div> -->
  </div>
</template>

<script>
import Movie from '@/components/Movie.vue';

const API_URL = 'https://omdb-api.now.sh/?type=movie&s=';

export default {
  name: 'app',
  components: {
    Movie,
  },
  data: () => ({
    error: '',
    searchTerm: '',
    results: [],
    favs: [],
  }),
  methods: {
    async getResults() {
      const url = `${API_URL}${this.searchTerm}`;
      const response = await fetch(url);
      const data = await response.json();
      if (data.Error) {
        this.results = [];
        this.error = data.Error;
      } else if (this.searchTerm === 'mandalorian') {
        this.results = data.Search;
        this.error = 'This is the way';
        // console.log(this.results);
      } else {
        this.results = data.Search;
        this.error = '';
        // console.log(this.results);
      }
    },
    addFav(movie) {
      if (this.favs.includes(movie) === false) {
        this.favs.push(movie);
      }
    },
    removeFav(movie) {
      const index = this.favs.indexOf(movie);
      this.favs.splice(index, 1);
    },
  },
};

</script>

<style>

</style>
