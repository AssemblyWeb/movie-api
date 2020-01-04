<template lang="html">
  <div class="px-2">
    <div class="rounded border shadow-lg overflow-hidden">
      <img class="object-cover w-full h-400" :src="getImgUrl(movie.Poster)"
        :alt='movie.Title'>
      <div class="px-6 py-4 h-auto relative">
        <div class="mb-4">{{movie.Title}} ({{movie.Year}})</div>
        <div class="absolute bottom-10">
          <a :href="'https://www.imdb.com/title/' + movie.imdbID" target="_blank"
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
            See movie
          </a>
          <a @click="addFav(movie)"
          class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white
          py-2 px-4 border border-blue-500 hover:border-transparent rounded">add</a>
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
        return 'favicon.ico';
      }
      return this.movie.Poster;
    },
  },
};
</script>

<style>
.bottom-10{
  bottom: 10px;
}
</style>
