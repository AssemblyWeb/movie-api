<template>
  <div class="w-full border-solid border-1 rounded shadow-lg">
    <div class="h-auto w-32 flex-none bg-cover rounded-t lg:rounded-t-none lg:rounded-l text-center bg-white overflow-hidden" :style="'background-image: url(' + getImgUrl(movie.Poster) + ')'" title="Woman holding a mug">
    </div>
    <div class="w-full bg-white p-4 flex flex-col justify-between leading-normal">
      <div class="mb-8">
        <div class="text-gray-900 font-bold text-xl">{{movie.Title}}</div>
        <div class="inline-block text-xs font-bold movie-card-category bg-green-200 uppercase text-green-500 rounded-full px-3">{{movie.Type}}</div>
      </div>
      <div class="flex items-center">
          <a @click="removeFav(movie)"
          class="bg-red-500 text-red-700 font-semibold border-red-500 movie-card-trash
          py-2 px-4 border hover:bg-transparent hover:border-red-500 rounded transition cursor-pointer">
            <svg xmlns="http://www.w3.org/2000/svg" width="18.359" height="20.982" viewBox="0 0 18.359 20.982">
              <path class="transition" id="trash-alt-regular" d="M10.983,17.048h.984a.492.492,0,0,0,.492-.492V7.7a.492.492,0,0,0-.492-.492h-.984a.492.492,0,0,0-.492.492v8.852A.492.492,0,0,0,10.983,17.048ZM17.7,3.278H14.326L12.933.955A1.967,1.967,0,0,0,11.245,0H7.114A1.967,1.967,0,0,0,5.427.955L4.033,3.278H.656A.656.656,0,0,0,0,3.934V4.59a.656.656,0,0,0,.656.656h.656V19.015a1.967,1.967,0,0,0,1.967,1.967h11.8a1.967,1.967,0,0,0,1.967-1.967V5.245H17.7a.656.656,0,0,0,.656-.656V3.934A.656.656,0,0,0,17.7,3.278ZM7.042,2.086a.246.246,0,0,1,.211-.119h3.852a.246.246,0,0,1,.211.119l.716,1.192H6.327Zm8.039,16.928H3.278V5.245h11.8ZM6.393,17.048h.984a.492.492,0,0,0,.492-.492V7.7a.492.492,0,0,0-.492-.492H6.393A.492.492,0,0,0,5.9,7.7v8.852A.492.492,0,0,0,6.393,17.048Z" transform="translate(0 0)" fill="#fff"/>
            </svg>
          </a>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  props: ['movie', 'removeFav'],
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
.movie-card-trash:hover svg path {
  fill: #f54d4d;
}
</style>
