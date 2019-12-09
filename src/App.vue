<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
      <a class="navbar-brand" href="#">Navbar</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse"
        data-target="#navbarColor01" aria-controls="navbarColor01" aria-expanded="false"
        aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarColor01">
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
            <div v-for="movie in results" :key="movie.id" class="card col-4">
                <div class="card-img-top movie-card"
                  v-bind:style='{ backgroundImage: "url(" + movie.Poster + ")", }'
                >
                </div>
                <h5 class="card-title">{{movie.Title}}</h5>
                <p class="card-text">
                  {{movie.Year}}
                </p>
                <a :href="'https://www.imdb.com/title/' + movie.imdbID" target="_blank" class="btn btn-danger">See movie</a>
                <a @click="addFav(movie)" class="btn btn-primary">add</a>
            </div>
          </div>
        </div>
        <div class="col-3">
          <div v-for="movie in favs" :key="movie.id">
              {{movie.Title}} {{movie.Year}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import Movie from '@/components/Movie';

const API_URL = 'https://omdb-api.now.sh/?type=movie&s=';

export default {
  name: 'app',
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
      } else {
        this.results = data.Search;
        this.error = '';
        // console.log(this.results);
      }
    },
    addFav(movie) {
      this.favs.push(movie);
    },
  },
};

</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: white;

  }
  .movie-card{
    min-height: 200px;
    background-size: cover;
  }

</style>
