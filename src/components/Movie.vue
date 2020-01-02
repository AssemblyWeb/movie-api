<template lang="html">
  <div class="rounded border shadow-lg overflow-hidden m-2">
    <img class="object-cover w-full h-42" :src="getImgUrl(movie.Poster)"
      :alt='movie.Title'>
    <div class="px-6 py-4">
      <div class="mb-2">{{movie.Title}} ({{movie.Year}})</div>
      <p class="">
        <a :href="'https://www.imdb.com/title/' + movie.imdbID" target="_blank"
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">See movie</a>
        <a @click="addFav(movie)" class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded">add</a>
      </p>
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
