<template>
  <div id="app">
    <nav class="flex bg-white items-center justify-between flex-wrap shadow-md p-6">
      <div class="flex items-center flex-shrink-0 text-white mr-6">
        <span class="font-semibold text-xl tracking-tight">
          <img src="@/assets/logo.svg" alt="">
        </span>
      </div>
      <form class="" @submit.prevent="getResults">
        <input v-model="searchTerm" class="transition focus:outline-0 border border-transparent
        focus:bg-white
        focus:border-gray-300 placeholder-gray-600 rounded-lg
        bg-gray-200 py-2 pr-4 pl-10 block w-full
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
      <div class="flex flex-grow mt-5 container mx-auto">
        <div class="w-3/4">
            <div v-if="this.results.length">
              {{this.results.length}} in "{{this.searchTerm}}"
            </div>
            <div class="container flex flex-wrap float-right m-2">
              <movie v-for="movie in results" :key="movie.id" class="w-1/3 mb-4"
              :movie="movie"
              :addFav="addFav"
              :removeFav="removeFav"
              >
              </movie>
            </div>
        </div>
        <!-- favs -->
        <div class="w-1/4">
        <div class="ml-1" v-if="this.favs.length">
          {{this.favs.length}} Favs
        </div>
         <div>
            <minicard v-for="movie in favs" :key="movie.id"
            :movie="movie" :removeFav="removeFav"
            class="flex w-3/3 m-2">
            </minicard>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
import Movie from '@/components/Movie.vue';
import Minicard from '@/components/Minicard.vue';

// const API_URL = 'https://omdb-api.now.sh/?type=movie&s=';
const API_URL = 'https://omdb-api.now.sh/?s=';

export default {
  name: 'app',
  components: {
    Movie,
    Minicard,
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
      console.log(this.favs);
    },
    removeFav(movie) {
      const index = this.favs.indexOf(movie);
      this.favs.splice(index, 1);
    },
  },
};

</script>

<style>
body{
  background-color: #EDF2F6;
}
</style>
