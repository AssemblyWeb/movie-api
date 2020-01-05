<template lang="html">
  <div class="px-2">
    <div class="rounded border shadow-lg bg-white h-auto overflow-hidden">
      <img class="object-cover w-full movie-card-img" :src="getImgUrl(movie.Poster)"
        :alt='movie.Title'>
      <div class="px-6 py-4 h-32 relative">
        <div class="mb-4">{{movie.Title}} ({{movie.Year}})</div>
        <div class="absolute movie-card-buttons">
          <a :href="'https://www.imdb.com/title/' + movie.imdbID" target="_blank"
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
            See movie
          </a>
          <a @click="addFav(movie)"
          class="bg-transparent hover:bg-red-500 text-red-700 font-semibold hover:text-white
          py-2 px-4 border border-red-500 hover:border-transparent rounded ml-2">❤️</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['movie', 'addFav', 'removeFav'],
  methods: {
    getImgUrl(poster) {
      if (poster === 'N/A') {
        return 'apimovie-missing.png';
      }
      return this.movie.Poster;
    },
  },
};
</script>

<style >
.movie-card-buttons{
  bottom: 20px;
}
.movie-card-img{
  height: 400px;
}
</style>
