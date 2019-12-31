<template>
  <div id="app" class="bg-red-500">
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary bg-red-500">
      <a class="navbar-brand" href="#">Vue.js search movie</a>
      <div class="" id="navbarColor01">
        <form @submit.prevent="getResults" class="form-inline my-2 my-lg-0">
          <input v-model="searchTerm" class="form-control mr-sm-2" type="text" placeholder="Search">
          <button class="btn btn-secondary my-2 my-sm-0" type="submit">Search</button>
        </form>
      </div>
    </nav>
    <div class="container">
      <div class="row mt-3">
        <div class="col-9">
          <div v-if="error" class="mt-3 alert alert-dismissible alert-danger">
            <strong>{{error}}</strong>
          </div>
          <div class="row">
            <movie v-for="movie in results" :key="movie.id" class="card col-4"
              :movie="movie"
              :addFav="addFav"
              :removeFav="removeFav"
            >
            </movie>
          </div>
        </div>
        <div class="col-3">
          <div v-for="movie in favs" :key="movie.id">
              {{movie.Title}} {{movie.Year}}
              <a @click="removeFav(movie)" class="btn btn-primary">remove</a>
          </div>
        </div>
      </div>
    </div>
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
