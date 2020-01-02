<template lang="html">
  <div class="max-w-sm rounded overflow-hidden shadow-lg">
    <img class="w-full" :src='movie.Poster'
      alt="Sunset in the mountains">
    <div class="px-6 py-4">
      <div class="font-bold text-xl mb-2">{{movie.Title}} ({{movie.Year}})</div>
      <p class="text-gray-700 text-base">
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
};
</script>
