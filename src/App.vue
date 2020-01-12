<template>
  <div id="app">
    <navbar
     v-model="searchTerm"
     :getResults="getResults"
    ></navbar>
      <div class="flex flex-grow mt-5 container mx-auto">
        <div class="w-3/4">
          <!-- error -->
          <error :error="error"
          ></error>
          <!-- show results -->
            <div class="font-primary" v-if="this.results.length">
              {{this.results.length}} matching results in <span class="font-bold">"{{this.matchingResult}}"</span>
            </div>
            <div class="container flex flex-wrap float-right m-2">
              <movie v-for="movie in results" :key="movie.id" class="w-1/3 mb-4"
              :movie="movie"
              :addFav="addFav"
              >
              </movie>
            </div>
        </div>
        <!-- favs -->
        <div class="w-1/4">
        <div class="ml-3 font-bold font-primary" v-if="this.favs.length">
          Movies to see: {{this.favs.length}}
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
import Navbar from '@/components/Navbar.vue';
import Error from '@/components/Error.vue';
import Movie from '@/components/Movie.vue';
import Minicard from '@/components/Minicard.vue';

const API_URL = 'https://www.omdbapi.com/?s=';
const key = '&apikey=33e16bf1';

export default {
  name: 'app',
  components: {
    Movie,
    Minicard,
    Navbar,
    Error,
  },
  data: () => ({
    error: '',
    searchTerm: '',
    results: [],
    favs: [],
    matchingResult: '',
  }),
  methods: {
    async getResults() {
      const url = `${API_URL}${this.searchTerm}${key}`;
      const response = await fetch(url);
      const data = await response.json();
      if (data.Error) {
        this.results = [];
        this.error = data.Error;
      } else if (this.searchTerm === 'mandalorian') {
        this.results = data.Search;
        this.error = 'This is the way';
        this.matchingResult = this.searchTerm;
      } else {
        this.results = data.Search;
        this.error = '';
        this.matchingResult = this.searchTerm;
        // console.log(this.results);
      }
    },
    addFav(movie) {
      if (this.favs.includes(movie) === false) {
        this.favs.push(movie);
      }
      // console.log(this.favs);
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
.transition{
  transition: all ease 0.3s;
}
.navbar-github:hover svg path{
  fill:#34495F;
}
.font-primary, .movie-card-title{
  color: #34495F;
}
.navbar-form-search{
  top: 12px;
  left: 12px;
}
.navbar-form input:focus{
  border-radius: 4px;
  outline-color: #3AB982;
}
</style>
