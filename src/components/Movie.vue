<template lang="html">
  <div class="px-2">
    <div class="rounded border shadow-lg bg-white h-auto relative overflow-hidden">
      <img class="object-cover w-full movie-card-img" :src="getImgUrl(movie.Poster)"
        :alt='movie.Title'>
      <div class="absolute inline-block text-xs font-bold movie-card-category bg-green-200 uppercase text-green-500 rounded-full px-3 ">{{movie.Type}}</div>
      <div class="px-6 py-4 h-32 relative">
        <div class="mb-4 movie-card-title">
          <span class="font-bold">{{movie.Title}}</span> ({{movie.Year}})
        </div>
        <div class="absolute movie-card-buttons h-10">
          <a :href="'https://www.imdb.com/title/' + movie.imdbID" target="_blank"
            class="inline-block uppercase hover:border-transparent border-green-500 border bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded transition cursor-pointer">
            More info
          </a>
          <addFav
            :addFav="addFav"
          ></addFav>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import AddFav from '@/components/buttons/AddFav.vue';

export default {
  components: {
    AddFav,
  },
  props: ['movie', 'addFav'],
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

<style>
.movie-card-buttons{
  bottom: 20px;
}
.movie-card-img{
  height: 400px;
}

.movie-card-category{
  top: 20px;
  left: 20px;
}
.movie-card-heart:hover svg path {
  fill: white;
}
</style>
