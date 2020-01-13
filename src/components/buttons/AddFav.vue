<template>
  <div @click="addFav(movie)"
  class="inline-block movie-card-heart bg-transparent hover:bg-red-500 text-red-700 font-semibold hover:text-white
  border border-red-500 hover:border-transparent rounded py-2 px-4 ml-2 cursor-pointer transition">
    <svg class="inline" xmlns="http://www.w3.org/2000/svg" width="24.25" height="21.218" viewBox="0 0 24.25 21.218">
      <path class="transition" id="heart-solid" d="M21.884,33.418a6.477,6.477,0,0,0-8.838.644l-.933.961-.933-.961a6.476,6.476,0,0,0-8.838-.644,6.8,6.8,0,0,0-.469,9.847l9.164,9.463a1.485,1.485,0,0,0,2.145,0l9.164-9.463a6.8,6.8,0,0,0-.464-9.847Z" transform="translate(0.012 -31.967)" fill="#f54d4d"/>
    </svg>
  </div>
</template>

<script>
export default {
  props: ['addFav'],
};
</script>
