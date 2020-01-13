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
          <div :href="'https://www.imdb.com/title/' + movie.imdbID" target="_blank"
            class="inline-block uppercase hover:border-transparent border-green-500 border bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded transition cursor-pointer">
            More info
          </div>
          <addFav
            :addFav="addFav"
          ></addFav>
          <!-- <div @click="addFav(movie)"
          class="inline-block movie-card-heart bg-transparent hover:bg-red-500 text-red-700 font-semibold hover:text-white
          border border-red-500 hover:border-transparent rounded py-2 px-4 ml-2 cursor-pointer transition">
            <svg class="inline" xmlns="http://www.w3.org/2000/svg" width="24.25" height="21.218" viewBox="0 0 24.25 21.218">
              <path class="transition" id="heart-solid" d="M21.884,33.418a6.477,6.477,0,0,0-8.838.644l-.933.961-.933-.961a6.476,6.476,0,0,0-8.838-.644,6.8,6.8,0,0,0-.469,9.847l9.164,9.463a1.485,1.485,0,0,0,2.145,0l9.164-9.463a6.8,6.8,0,0,0-.464-9.847Z" transform="translate(0.012 -31.967)" fill="#f54d4d"/>
            </svg>
          </div> -->
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
