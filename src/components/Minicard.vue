<template>
  <div class="w-full">
    <div class="h-auto w-32 flex-none bg-cover rounded-t lg:rounded-t-none lg:rounded-l text-center overflow-hidden" :style="'background-image: url(' + getImgUrl(movie.Poster) + ')'" title="Woman holding a mug">
    </div>
    <div class="border-r w-full border-b border-l border-gray-400 lg:border-l-0 lg:border-t lg:border-gray-400 bg-white rounded-b lg:rounded-b-none lg:rounded-r p-4 flex flex-col justify-between leading-normal">
      <div class="mb-8">
        <div class="text-gray-900 font-bold text-xl mb-2">{{movie.Title}}</div>
      </div>
      <div class="flex items-center">
                  <a @click="removeFav(movie)"
          class="bg-transparent hover:bg-red-500 text-red-700 font-semibold hover:text-white
          py-2 px-4 border border-red-500 hover:border-transparent rounded ml-2">remove</a>
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
